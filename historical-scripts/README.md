# Historical J-release deployment helpers

These three files come from local files found in `/root/ric-dep/bin` of the Ubuntu VM. The shell files had trailing whitespace cleaned for Git; their commands and parameters are otherwise unchanged. They preserve the old package versions, absolute path, and static IP used during the experiment. They have not been modernized or executed during portfolio preparation.

`install_k8s_docker_helm.sh` resets Kubernetes, removes installed packages, changes system configuration, and initializes a cluster. `install_kong.sh` edits many upstream files and removes ingress templates. Read them as source artifacts; do not run them on a machine with data or an existing cluster without a full review.

The two shell files passed `bash -n` syntax checks in the VM. That check does not establish successful installation. See [implementation notes](../docs/implementation.md) for the specific settings these scripts changed.
