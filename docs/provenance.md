# Sources and provenance

The VM retained upstream Git checkouts with local, uncommitted changes. The commit IDs below are the checked-out upstream bases, **not** commits that contain the local changes. Paths refer to the original Ubuntu VM.

| VM directory | Upstream origin | Checked-out commit | Portfolio treatment |
| --- | --- | --- | --- |
| `/root/ric-dep` | [O-RAN SC `ric-plt/ric-dep`](https://gerrit.o-ran-sc.org/r/admin/repos/ric-plt/ric-dep) | `505e5efb5f40706adccdfdc7a5289456cd01fe8a` | Local untracked helper scripts and kubeadm config preserved; material configuration differences summarized. |
| `/root/dep` | [O-RAN SC `it/dep`](https://gerrit.o-ran-sc.org/r/admin/repos/it/dep) | `68332a494ab572e3b526c799aa7389810451749b` | PMS and recipe differences summarized; sanitized examples provided. |
| `/root/ranpm` | [O-RAN SC `nonrtric-plt-ranpm`](https://github.com/o-ran-sc/nonrtric-plt-ranpm) | `bf779f6b82c5d7f7cc4cd6f5d01c347c51b45e51` | Local Helm changes described as an extension. |
| `/root/smart5g-ranpm` | [ONF `smart5g-nonrtric-plt-ranpm`](https://github.com/opennetworkinglab/smart5g-nonrtric-plt-ranpm) | `dbf86a2b6fb857d98ebfdae1971f0e5e22b60bea` | Local rApp and Helm experiments summarized; generated certificates and private keys excluded. |
| `/root/oam` | [O-RAN SC `oam`](https://gerrit.o-ran-sc.org/r/admin/repos/oam) | `1dcbd86bcea1ebf23ed42f57f936a48d4d445133` | Environment-specific `.env` and Compose changes excluded. |
| `/root/rappmanager` | [O-RAN SC `nonrtric/plt/rappmanager`](https://gerrit.o-ran-sc.org/r/admin/repos/nonrtric/plt/rappmanager) | `ffd5b45b53572ae42fbc22510bcbe3ad8883b86f` | Referenced as an upstream dependency; generated/local installation files excluded. |

The original notes are [Near-RT RIC F-release](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/HJbMQEgYn), [F-release Non-RT/Near-RT connection](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/BkkQb8UWA), [J-release RIC deployment](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/S1Dij0ABR), and [RAN PM/rApps](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/HkeIBWmvC).

This portfolio includes a small set of local files and screenshots. It excludes cloned upstream source trees, VM/OVA images, container images, runtime data, generated keys/certificates, environment files, and the raw working-tree patches. The scripts in `historical-scripts/` are kept to show the historical work, with their original local parameters intact. The `examples/` files were edited for publication and are not exact VM copies.
