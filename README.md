# What is this?
This is a frok of the Compulab Linux repository, containing a branch made just for us, that enables some kernel modules (mostly CONFIG_NFT_COUNTER) for compatibility with the Avassa Edge Enforcer. Compulab said that they would keep this branch, until the end of 2025, so it has been forked here, so that we can always have it. 

# Kernel Build Manual

## Prerequisites
It is up to developers to prepare the host machine; it requires:

* [Setup Cross Compiler](https://github.com/compulab-yokneam/meta-bsp-imx8mp/blob/kirkstone/Documentation/toolchain.md#linaro-toolchain-how-to)

## CompuLab Linux Kernel setup

* WorkDir:
```
mkdir -p compulab-kernel/build && cd compulab-kernel
```

* Set a CompuLab machine:

| Machine | Command Line |
|---|---|
|ucm-imx8m-plus|```export MACHINE=compulab_v8```|
|som-imx8m-plus|```export MACHINE=compulab_v8```|
|iot-gate-imx8plus|```export MACHINE=compulab_v8```|
|iotdin-imx8p|```export MACHINE=compulab_v8```|
|ucm-imx93|```export MACHINE=ucm-imx93```|

* Clone the source code:
```
git clone -b linux-compulab_v6.1.22 https://github.com/compulab-yokneam/linux-compulab.git
cd linux-compulab
```

## Compile the Kernel

* Apply the default CompuLab config:
```
make ${MACHINE}_defconfig compulab.config
```

* Ussue menuconfig on order to change the default CompuLab configuration:
```
make menuconfig
```

* Build the kernel
```
nice make -j`nproc`
```

* [Deploy the CompuLab Linux Kernel to CompuLab devices](https://github.com/compulab-yokneam/Documentation/blob/master/etc/linux_kernel_deployment.md#create-deb-package)
