# Sources and provenance

The VM retained upstream Git checkouts with local, uncommitted changes. The commit IDs below are the checked-out upstream bases, **not** commits that contain the local changes. Paths refer to the original Ubuntu VM.

| VM directory | Upstream origin | Checked-out commit | Snapshot and local work |
| --- | --- | --- | --- |
| `/root/ric-dep` | [O-RAN SC `ric-plt/ric-dep`](https://gerrit.o-ran-sc.org/r/admin/repos/ric-plt/ric-dep) | `505e5efb5f40706adccdfdc7a5289456cd01fe8a` | [Source](../source/ric-dep/) includes local setup helpers and configuration; [patches](../changes/README.md) isolate tracked edits. |
| `/root/dep` | [O-RAN SC `it/dep`](https://gerrit.o-ran-sc.org/r/admin/repos/it/dep) | `68332a494ab572e3b526c799aa7389810451749b` | [Source](../source/dep/) includes PMS and recipe edits; a sanitized [PMS example](../examples/pms-application-configuration.example.json) is separate. |
| `/root/ranpm` | [O-RAN SC `nonrtric-plt-ranpm`](https://github.com/o-ran-sc/nonrtric-plt-ranpm) | `bf779f6b82c5d7f7cc4cd6f5d01c347c51b45e51` | [Source](../source/ranpm/) includes Helm edits, excluding a changed client secret. |
| `/root/smart5g-ranpm` | [ONF `smart5g-nonrtric-plt-ranpm`](https://github.com/opennetworkinglab/smart5g-nonrtric-plt-ranpm) | `dbf86a2b6fb857d98ebfdae1971f0e5e22b60bea` | [Source](../source/smart5g-ranpm/) includes experimental rApp/O1 edits, excluding generated TLS material and a changed secret. |
| `/root/smart5g-ranpm/smart5g-sim-o1` | [ONF `smart5g-sim-o1-interface`](https://github.com/opennetworkinglab/smart5g-sim-o1-interface) | `09a24838d34b5464ba2247a879257f716b7d0429` | Nested [O1 simulator source](../source/smart5g-ranpm/smart5g-sim-o1/) included without its Git history or local environment files. |
| `/root/oam` | [O-RAN SC `oam`](https://gerrit.o-ran-sc.org/r/admin/repos/oam) | `1dcbd86bcea1ebf23ed42f57f936a48d4d445133` | [Source](../source/oam/) includes the local Compose change; `.env` files and downloaded runtime applications are excluded. |
| `/root/rappmanager` | [O-RAN SC `nonrtric/plt/rappmanager`](https://gerrit.o-ran-sc.org/r/admin/repos/nonrtric/plt/rappmanager) | `ffd5b45b53572ae42fbc22510bcbe3ad8883b86f` | [Source](../source/rappmanager/) included; a local PID file and uninitialized submodule are excluded. |

The original notes are [Near-RT RIC F-release](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/HJbMQEgYn), [F-release Non-RT/Near-RT connection](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/BkkQb8UWA), [J-release RIC deployment](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/S1Dij0ABR), and [RAN PM/rApps](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/HkeIBWmvC).

This portfolio includes [source-tree snapshots](../source/), [working-tree patches](../changes/), local files, and screenshots. It excludes upstream `.git` histories, VM/OVA images, container images, downloaded runtimes, environment files, generated keys/certificates, and secret-bearing values. The scripts in `historical-scripts/` preserve the historical work with their original local parameters; the `examples/` files were edited for publication and are not exact VM copies. See the [source guide](../source/README.md) for omissions that affect reproducibility.
