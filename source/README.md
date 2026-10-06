# Source snapshots from the VM

This directory contains the application source trees as they existed in the Ubuntu VM, including the VM's local working-tree changes. The publishable snapshot contains 3,831 files across six checkouts. The original Git history stays with the VM; the checked-out upstream commit IDs and origin links are recorded in [provenance](../docs/provenance.md). The commit IDs identify the base versions, not the local changes.

| Directory | Files | Role in the lab |
| --- | ---: | --- |
| [`ric-dep/`](ric-dep/) | 690 | Near-RT RIC deployment, charts, Kubernetes operator, and local setup helpers. |
| [`dep/`](dep/) | 1,092 | Non-RT RIC deployment, PMS configuration, recipes, and a local chart draft. |
| [`ranpm/`](ranpm/) | 539 | O-RAN SC RAN PM components and Helm setup. |
| [`smart5g-ranpm/`](smart5g-ranpm/) | 928 | ONF RAN PM/rApp experiment, including the nested O1 simulator checkout. |
| [`oam/`](oam/) | 304 | OAM/SMO source and Compose configuration. |
| [`rappmanager/`](rappmanager/) | 278 | rApp Manager source used as a related dependency. |

Most files in these trees come from the credited upstream projects. The [change patches](../changes/README.md) isolate the local edits found in the VM. Files such as `es-rapp/main.py`, the PMS configuration, and the installation helpers are included in their original directory positions so the code can be browsed with its surrounding project structure.

## Publication exclusions

The snapshot excludes `.git` directories, VM and container images, downloaded executables, untracked generated Helm packages, Jenkins runtime files, environment files, runtime tokens, password and keystore files, private keys, certificates, and two Helm values files with changed client secrets. A few small upstream-tracked Helm test archives remain. Seven VM symlinks were omitted during transfer, including an absolute link into `/root`; some uninitialized Git submodule paths are also absent. The original VM remains the complete archive.

Some upstream source files contain example credentials and test tokens already present in the public projects. These are source fixtures, not credentials from this VM. The snapshot was checked for private-key blocks and common live-token formats before publication. No deployment or integration test was rerun during this transfer.
