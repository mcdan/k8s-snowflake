# k8s-configs

Configs and scripts for bootstrapping a Kubernetes cluster anywhere.

> **NOTE:** current support is only for Azure.

## Provisioning

These are **opinionated scripts**. If you don't like my opinions maybe consider
using one of the hundred-thousand other tools for provisioning a cluster.

I literally made this _because_ I didn't like the opinion of other things... so
here we are. :P

I purposely tried to keep this as minimal and simple as possible from the OS
base up.

Every node uses [Intel's Clear Linux](https://clearlinux.org/) as the base.
This is for reasons of security and performance. If you would like to learn
more on that you should click the link previously to their site.

Kubernetes is installed with [`RBAC`](https://kubernetes.io/docs/admin/authorization/rbac/)
and is set up with sane defaults. [TODO: more on this]

This cluster uses [`cri-containerd`](https://github.com/kubernetes-incubator/cri-containerd)
with [`runc`](https://github.com/opencontainers/runc) as the container
runtime. They also use [`cilium`](https://github.com/cilium/cilium)
as a networking plugin.

If you are wondering why I didn't use something like `cloud-init` it's because
Clear Linux has a pretty weirdly behaving version of `cloud-init` and I love
bash, m'kay.

### Azure

Make sure you have the `az` tool installed. You can find instructions on
downloading that
[here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest).

Make sure you are logged in.

To provision your cluster, clone this repo and run:

```console
$ ./azure/setup.sh
```

The you can ssh into the master node and you are all good to go!

## Acknowledgements

Thanks to [@kelseyhightower](https://github.com/kelseyhightower) for
[kubernetes-the-hard-way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
which helped a lot of this.
