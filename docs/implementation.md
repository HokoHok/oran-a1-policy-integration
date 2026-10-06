# J-release implementation notes

These observations come from the VM's local files and Git working-tree differences, compared with the upstream commits listed in [provenance](provenance.md). They describe what was present in the VM when this portfolio was prepared. A changed file alone is not proof that the same version was deployed successfully.

## Historical sequence

1. Prepare the Ubuntu VM with the pinned Docker, Kubernetes, and Helm versions; configure the pod subnet and ingress address.
2. Adapt `ric-dep` for the cluster, deploy standalone Kong, then deploy the Near-RT RIC and inspect A1 Mediator status.
3. Change the Non-RT RIC PMS target and deployment recipe, deploy the selected services, then query PMS for discovered RICs.
4. Create A1 policy type `20008` and register a service. The J-release notes stop short of a verified policy instance-to-xApp result.

This is the order described by the [J-release notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/S1Dij0ABR), not a newly tested installation procedure. The archived scripts change host packages and cluster state, so the steps are presented for understanding rather than direct execution.

## Near-RT RIC (`/root/ric-dep`)

| VM file or group | Local change | Why it mattered |
| --- | --- | --- |
| `bin/install_k8s_docker_helm.sh` | Local helper pins Kubernetes `1.28.1-1.1`, Docker `20.10.21-0ubuntu1~22.04.3`, Helm `3.14.2`, and the VM's former static IP. | Establishes the toolchain used by the experiment. |
| `bin/kubeadm-config.yaml` | Defines Kubernetes `v1.28.1`, pod subnet `10.244.0.0/16`, and `cgroupfs` for kubelet. | Records the intended single-node cluster configuration. |
| `bin/install_kong.sh` | Applies broad `v1beta1` → `v1` replacements, disables bundled Kong, removes three ingress templates, and installs standalone Kong. | Adapts old charts to the local cluster. The broad replacement must be reviewed before reuse. |
| `RECIPE_EXAMPLE/example_recipe_oran_j_release.yaml` | Changes `extsvcplt.ricip` from the upstream example address to the VM's address. | Makes the recipe specific to the historical VM. |
| `helm/infrastructure/values.yaml` | Changes `kong.enabled` from `true` to `false`. | Matches the standalone Kong approach. |

The VM has 50 tracked changes in `ric-dep`, many caused by the broad API-version replacement in bundled Kong/Prometheus templates. Forty-nine of those changes are preserved as [core and chart patches](../changes/README.md); the static-address recipe is omitted. The complete upstream trees remain in the VM. The selected local helper scripts are preserved under [`historical-scripts/`](../historical-scripts/).

## Non-RT RIC (`/root/dep`)

| VM file or group | Local change | Why it mattered |
| --- | --- | --- |
| `nonrtric/helm/policymanagementservice/resources/data/application_configuration.json` | Replaces six A1 simulator entries with an A1 Mediator target. | Points PMS at the Near-RT RIC. |
| `nonrtric/RECIPE_EXAMPLE/example_recipe.yaml` | Disables the A1 simulator, O-RU FH recovery, and RAN slice assurance; enables the DME participant; lengthens PMS startup probes. | Narrows the deployment and allows more startup time. |
| `nonrtric/helm/a1controller/{values.yaml,templates/deployment.yaml}` | Lengthens probes and adds CPU/memory requests and limits. | Adjusts controller startup and scheduling. |
| `RECIPE_EXAMPLE/{Chart.yaml,values.yaml}` | New local chart files are present. | Records a local dependency setup; these drafts were not selected as a runnable chart. |

The PMS JSON parses, but the VM's `customAdapterClass` contains a space after `clients.`. The [published example](../examples/pms-application-configuration.example.json) removes that likely typo, replaces the historical endpoint with a placeholder, and replaces the controller password. It has **not** been runtime-validated. The [recipe excerpt](../examples/nonrtric-recipe-excerpt.yaml) reflects the current VM file, rather than the broader component selection in one draft `values.yaml`.

## How to read the screenshots

The historical Non-RT RIC screenshot shows A1 simulator pods and other components that the current recipe excerpt disables. It also shows some unhealthy pods. The screenshot and present working-tree files therefore represent different experiment states. See [evidence](evidence.md) for the exact claims supported by each record.
