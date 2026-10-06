# RAN PM and rApp extension

This was a later experiment alongside the A1 integration work. It is documented separately because the available records do not prove a complete PM data pipeline.

The VM contains two distinct upstream checkouts: O-RAN SC `nonrtric-plt-ranpm` under `/root/ranpm` and ONF `smart5g-nonrtric-plt-ranpm` under `/root/smart5g-ranpm`. Local differences include:

- Kafka version adjustments. The `/root/ranpm` working tree specifies `3.7.1`; the HackMD troubleshooting example shows `3.7.0`, so they should be treated as different experiment states.
- Renaming the additional information service to `informationservice-ranpm` to avoid colliding with the existing Non-RT RIC service.
- Local container-image and O1 simulator settings, plus changes to the `es-rapp` Python program and Helm templates.

The [RAN PM/rApp notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/HkeIBWmvC) record installation and troubleshooting steps and explicitly mark the PM connection procedure as deferred. Generated certificates, private keys, tokens, and environment-specific Helm values remain in the VM archive and are not part of this portfolio repository.

The [RAN PM source](../source/ranpm/) and [ONF experiment source](../source/smart5g-ranpm/) can be browsed in full context; the corresponding [RAN PM patch](../changes/ranpm.patch) and [rApp/O1 patch](../changes/smart5g-ranpm-experimental.patch) isolate local code and configuration differences. The changed `es-rapp/main.py` includes new cell selection and administrative-state requests, but those paths were not retested during this cleanup and should not be presented as a verified complete pipeline.
