---
title: ROS Install
layout: os-default
---

## ROS Install
---

The `ros install` command is used to install RancherOS to hard disk. Please follow the [guide]({{site.baseurl}}/os/running-rancheros/server/install-to-disk/) for an example of how to install to disk.

### Options

 Options | Description
---------|------------------------------------------------------------------------
 `--image`, `-i`      | Install RancherOS from a specific image
`--cloud-config`, `-c`      | The [Cloud-Config file]({{site.baseurl}}/os/cloud-config/) needed for SSH authorized keys
`--device`,  `-d`      | Which Device to Install to
`--force`,  `-f`      | [ DANGEROUS! Data loss can happen ] Partition/Format without prompting
`--install-type`, `-t`      | Install type:
         |   `generic`    - (default) creates 1 ext4 partition and installs RancherOS
         |   `amazon-ebs` - installs RancherOS and sets up PV-GRUB
`--no-reboot`      | Do not reboot after install

#### Image / Version

The `-i` option specifies the particular image to install from. By default, `ros install` uses the same installer image version as the ISO it is run from. E.g. for RancherOS v0.5.0 the default installer image would be `rancher/os:v0.5.0`.

You can use `ros os list` command to find the list of available RancherOS images/versions.
 
```bash
$ sudo ros os list
rancher/os:v0.4.0 remote
rancher/os:v0.4.1 remote
rancher/os:v0.4.2 remote
rancher/os:v0.4.3 remote
rancher/os:v0.4.4 remote
rancher/os:v0.4.5 remote
rancher/os:v0.5.0 remote
```

#### Cloud-Config

The `-c` option provides the location of the cloud config file. Read more about [cloud config files]({{site.baseurl}}/os/cloud-config).

#### Device

The `-d` option provides the target disk location. 

You can see the list of disks available to install to by running `sudo fdisk -l`

```bash
$ sudo fdisk -l
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 *512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table
```

#### Install Type
The `-t` option determines what type of installation is used. The `amazon-ebs` type is for creating your own AMI images. Since we are creating the [RancherOS AMI images]({{site.baseurl}}/os/running-rancheros/cloud/aws/), there is no need to create your own. 

By default, the install type will be `generic`.
