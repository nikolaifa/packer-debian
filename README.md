# Packer templates for Debian and Ubuntu

Original debian repo: https://github.com/quarkslab/packer-debian
\
which is based on: https://github.com/boxcutter/debian


Orignal ubuntu repo: https://github.com/boxcutter/ubuntu/

Original windows repo: https://github.com/juju4/windows

1. [Generate Boxes](#generate-boxes)
    1. [Debian 9.0.0 AMD64](#debian-900-amd64)
    2. [Ubuntu 18.04.2 AMD64](#ubuntu-18042-amd64)
2. [Security](#security)
    1. [SHA256](#sha256)


## Generate Boxes

Don't forget to download in the directory the ISO file listed in the debian-X.X.X-amd64.json or ubuntu-XX.XX.X-amd64 file.

### Debian 9.0.0 AMD64
```bash
    $ packer-io build -only=vmware-iso -var-file=debian-9.0.0-amd64.json debian.json
```

### Ubuntu 18.04.2 AMD64
```bash
    $ packer-io build -only=vmware-iso -var-file=ubuntu-18.04.2-amd64.json ubuntu.json
```

### Troubleshooting

Be careful with VMWare provider, they may need a manual task to do:
- When the mirror selection fail, click on "Go back"
- Go back to the "selection step menu"
- Select the "Configure Network" and then it should not fail again


## Security

### SHA256

To improve security, you can take advantage of the
``config.vm.box_download_checksum`` [Vagrantfile
option](https://docs.vagrantup.com/v2/vagrantfile/machine_settings.html).

First, you need to verify the integrity of the checksums. As they are part of
the `README.md` file, you need to verify the integrity of this file (See [Security/PGP](#pgp)):
