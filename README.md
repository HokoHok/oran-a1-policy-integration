# O-RAN A1 Policy Integration Lab

This repository documents a historical O-RAN Software Community integration lab. The main experiment connected the J-release Non-RT RIC Policy Management Service (PMS) to the Near-RT RIC A1 Mediator. Earlier F-release policy and Traffic Steering work, plus a later RAN PM/rApp experiment, are recorded separately.

The repository is a **portfolio record of the 2023–2024 work**, not a maintained deployment package. The original VirtualBox machine remains the archive. The stack was not redeployed or functionally tested during this repository cleanup.

## What the work covered

```mermaid
flowchart LR
    PMS[Non-RT RIC<br/>Policy Management Service] -->|A1 policy API| A1[Near-RT RIC<br/>A1 Mediator]
    A1 -. F-release experiment .-> XAPP[Traffic Steering xApp]
```

- Adapted J-release Kubernetes and Helm deployment settings for a local Ubuntu VM, including Kong and ingress changes.
- Replaced the PMS simulator targets with a local A1 Mediator entry and adjusted Non-RT RIC component selection and startup probes.
- Recorded API checks for RIC discovery, policy type `20008`, and service registration. The J-release notes do **not** establish delivery of a policy instance to an xApp.
- Previously recorded policy instance `1000` and Traffic Steering xApp work on **F-release**. This is a separate experiment.
- Explored O1 simulation and RAN PM/rApps. The available notes do not establish a complete PM data pipeline.

## Repository guide

| Path | Contents |
| --- | --- |
| [`changes/`](changes/) | Five patches preserving 76 local changes across the upstream working trees, with scope and exclusions explained in the [change guide](changes/README.md). |
| [`historical-scripts/`](historical-scripts/) | Local J-release installation helpers and kubeadm configuration copied from the VM. These are archival scripts with destructive setup steps. |
| [`examples/`](examples/) | Small, sanitized A1/PMS configuration examples derived from the VM and notes. They are documentation excerpts, not a complete Helm recipe. |
| [`evidence/`](evidence/) | Selected screenshots from the original HackMD notes, with version and limitations explained in [evidence notes](docs/evidence.md). |
| [`docs/implementation.md`](docs/implementation.md) | Exact local configuration changes found in the VM. |
| [`docs/provenance.md`](docs/provenance.md) | Upstream repositories, VM commit IDs, and inclusion decisions. |
| [`docs/ran-pm-experiment.md`](docs/ran-pm-experiment.md) | Scope and status of the later RAN PM/rApp experiment. |

## Evidence and limits

The [J-release notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/S1Dij0ABR) show a Near-RT RIC pod snapshot, an `AVAILABLE` RIC response from PMS, a policy type listing containing `20008`, and a service registration response. The Non-RT RIC pod snapshot also shows components that were not healthy. The [F-release connection notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/BkkQb8UWA) show a policy instance in the control panel. [Evidence details](docs/evidence.md) distinguish these observations from the current VM state.

The local VM used Ubuntu 22.04-era packages, Kubernetes `1.28.1`, Docker `20.10.21`, and Helm `3.14.2`, according to its installation helper. Its original static addresses and available memory differ from a new machine. Recreating the full deployment would require checking dependency availability, resource requirements, and network configuration. No current compatibility claim is made.

## Attribution

The RIC, Non-RT RIC, and RAN PM platforms are upstream projects. This repository preserves local working-tree changes, scripts, configuration examples, and experiment evidence; it does not claim authorship of upstream platform code. See [provenance](docs/provenance.md) for links and commit IDs.
