# Vagrant-Terraform-ESXi-Environment

This is a Vagrant script to create a Terraform environment with the [ESXi Terraform Provider](https://github.com/josenk/terraform-provider-esxi) plugin. This will will work cross-platform (Windows, Linux, Mac) with minimal configuration, as long as you have Vagrant.

## Dependencies:

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (Version 5.2.18 confirmed working)
* [Vagrant](https://www.vagrantup.com/downloads.html) (version 2.2.2 confirmed working)
* The OVF Tool Linux bundle. Instructions below if you do not already have it.

## Instructions

1. Clone this repository.
2. Download ovftool 4.3 from the [VMWare website](https://www.vmware.com/support/developer/ovf/) and store the .bundle file (e.g. `VMware-ovftool-4.3.0-7948156-lin.x86_64.bundle`) in the cloned repository directory. Unfortunately, you need a VMWare login to download this file. 
3. Run `vagrant up` in the cloned repository directory. 
4. When vagrant has completed virtual machine creation, ssh into the VM using `vagrant ssh`.
5. After you ssh into the VM you can navigate to the mounted Git repository directory by using `cd /vagrant`. From here you can call `terraform` commands against configurations stored on your computer. See [here](https://github.com/josenk/terraform-provider-esxi) for an example ESXi configuration.

## References
* [ESXi Terraform Provider](https://github.com/josenk/terraform-provider-esxi)

