# Linuxkit recipes for embedding unikernels in a minimal Linux

## Linuxkit ?

It's a tool to assemble minimal and secure linux images using container features.

See https://github.com/linuxkit/linuxkit

## How to use

* Build the `solo5` package: `linuxkit pkg build pkg/solo5`
* Once the build is done, an image such as `linuxkit/solo5:e1863083744015052785919f476a47fec6bc9048` should be obtained.
* This image should match the `solo5` service image in `linuxkit.yml`
* Then, perform the linuxkit build: `linuxkit build linuxkit.yml`

Running:
* `linuxkit run linuxkit` launches QEMU on Linux but doesn't enable nested virtualization.
* `./run.sh` performs the same QEMU command but adds `-cpu host` to enable nested virtualization.

Checking that it works inside the shell:
* `ctr -n services.linuxkit task attach solo5` and see the hello world

## WIP

`linuxkit-tap-networking` is my current experiment where Linux is set up with a tap interface assigned to the solo5 unikernel.
It doesn't work yet.

### Note

Inside the shell, use `export CONTAINERD_NAMESPACE=services.linuxkit` to use `ctr` with the correct namespace.
