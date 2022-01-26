<img alt="Rook" src="media/logo.svg" width="50%" height="50%">

# kubectl-rook-ceph

Provide common management and troubleshooting tools for the [Rook Ceph](https://github.com/rook/rook) storage provider as a [Krew](https://github.com/kubernetes-sigs/krew) plugin.

## Install

To install the plugin, run:

  ```kubectl krew install rook-ceph```

## Usage

`kubectl rook-ceph <root-args> <command> <command-args>`

### Root args

- `--namespace` | `-n`: the Kubernetes namespace in which the CephCluster resides (default: rook-ceph)
- `--help` | `-h`: Output help text

### Commands

- `ceph`: Run a Ceph CLI command. Supports any arguments the `ceph` command supports. See [Ceph docs](https://docs.ceph.com/en/pacific/start/intro/) for more.

- `operator`: run sub-commands against the Rook-Ceph operator
  -  `restart`: restart the Rook-Ceph operator

- `help`: Output help text


## Examples

### Run a Ceph Command

Any `ceph` command can be run with the plugin. This example gets the ceph status:

```console
kubectl rook-ceph ceph status
```

>```text
>  cluster:
>    id:     a1ac6554-4cc8-4c3b-a8a3-f17f5ec6f529
>    health: HEALTH_OK
>
>  services:
>    mon: 3 daemons, quorum a,b,c (age 11m)
>    mgr: a(active, since 10m)
>    mds: 1/1 daemons up, 1 hot standby
>    osd: 3 osds: 3 up (since 10m), 3 in (since 8d)
>
>  data:
>    volumes: 1/1 healthy
>    pools:   6 pools, 137 pgs
>    objects: 34 objects, 4.1 KiB
>    usage:   58 MiB used, 59 GiB / 59 GiB avail
>    pgs:     137 active+clean
>
>  io:
>    client:   1.2 KiB/s rd, 2 op/s rd, 0 op/s wr
>```

### Restart the Operator

```console
kubectl rook-ceph operator restart
```

>```text
>deployment.apps/rook-ceph-operator restarted
>```

## Contributing

We welcome contributions. See the [Rook Contributing Guide](https://github.com/rook/rook/blob/master/CONTRIBUTING.md) to get started.

## Report a Bug

For filing bugs, suggesting improvements, or requesting new features, please open an [issue](https://github.com/rook/kubectl-rook-ceph/issues).

## Contact

Please use the following to reach members of the community:

- Slack: Join our [slack channel](https://slack.rook.io)
- Forums: [rook-dev](https://groups.google.com/forum/#!forum/rook-dev)
- Twitter: [@rook_io](https://twitter.com/rook_io)
- Email (general topics): [cncf-rook-info@lists.cncf.io](mailto:cncf-rook-info@lists.cncf.io)
- Email (security topics): [cncf-rook-security@lists.cncf.io](mailto:cncf-rook-security@lists.cncf.io)

## Licensing

Rook is under the Apache 2.0 license.

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Frook%2Frook.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Frook%2Frook?ref=badge_large)
