# Local changes recovered from the VM

The files here are **Git diffs of the VM's local working trees**, relative to the upstream commits in [provenance](../docs/provenance.md). They isolate the local edits from the [full source snapshots](../source/README.md). Paths inside each patch are relative to its named upstream checkout.

| Patch | VM checkout | Changed paths | What it shows |
| --- | --- | ---: | --- |
| [Near-RT RIC core](ric-dep-core.patch) | `/root/ric-dep` | 10 | Operator API-version edits, removed ingress templates, standalone Kong setting, and ingress-related templates. |
| [Chart compatibility edits](ric-dep-chart-compatibility.patch) | `/root/ric-dep` | 39 | Mostly broad Kubernetes API-version substitutions in bundled Kong, Prometheus, and InfluxDB charts, including generated snapshots and upstream documentation. |
| [Non-RT RIC](dep-nonrtric.patch) | `/root/dep` | 4 | Component selection, A1 controller resources and probes, and the PMS target change from simulators to A1 Mediator. |
| [RAN PM](ranpm.patch) | `/root/ranpm` | 8 | Kafka version, local image settings, and Information Service renaming. |
| [Experimental rApp/O1 work](smart5g-ranpm-experimental.patch) | `/root/smart5g-ranpm` | 15 | `es-rapp` Python decision logic, O1/PM Helm settings, and installation scripts. |

These five patches cover **76 changed upstream paths**. This is a count of differences, not 76 newly authored files or 76 independently validated changes. The historical install helpers are separately available in [`historical-scripts/`](../historical-scripts/), and the published PMS configuration is a sanitized [example](../examples/pms-application-configuration.example.json).

The VM also contains local changes omitted from these patches: its static-address recipe, an absolute-path symlink, a changed producer client secret, a generated TLS certificate and private key, and another secret-bearing producer value. The recipe is present in [`source/ric-dep/`](../source/ric-dep/); credentials, generated data, and Git histories remain in the VM. The Non-RT RIC patch still contains a historical private cluster address; it is an archival diff, not a portable deployment configuration.

**Validation limit:** Git parsed the patch files and their changed-path statistics. The patches were not applied to fresh checkouts or tested as a deployment. In particular, the chart-wide API substitutions may need schema changes beyond replacing version strings. The `es-rapp` patch is experimental code from the VM, not proof that its cell-control logic worked end to end.
