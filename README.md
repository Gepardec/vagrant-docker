![](https://img.shields.io/badge/license-GPL%20v3.0-brightgreen.svg)
![Maintenance](https://img.shields.io/maintenance/yes/2020)
<p align="right">
<img alt="gepardec" width=100px src="https://www.gepardec.com/files/gepardec_logo_light_background@2000w.png">
</p>
<br>
<br>

# vagrant-docker

We love to container. To get started with container is easy. Almost any OS for your workstation now supports docker. Just install it and you can get started. But for a training / test environment it is best if everybody uses the exact same setup. The goal is to have a common environment in which we can work and fix errors once if they occur, not on a per participant basis. As a logical consequencee we have put docker into a CentOS 7 based VM that can easily be managed via vagrant.

## Preflight

You can run our container training environment on your workstation once you have 

* [Vagrant](https://www.vagrantup.com/intro/getting-started/install.html)
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or Hyper-V for Windows

installed and downloaded this git repo. 


## Quickstart

To bootstrap the CentOS 7 VM with docker simply run.

```
vagrant up
```

**Hint:** Windows user working with hyper-v can either add the `--provider hyperv` option to use hyper-v as provider if virtualbox is installed as well or set hyper-v default in the usercontext by setting the user environment variable in powershell via `[Environment]::SetEnvironmentVariable("VAGRANT_DEFAULT_PROVIDER", "hyperv", "User")`. Further documentation can be found here: https://docs.microsoft.com/en-us/virtualization/community/team-blog/2017/20170706-vagrant-and-hyper-v-tips-and-tricks 
 
To work with the environment you can connect to it via

```
vagrant ssh
```

once connected you are connected to the CentOS VM and can run your docker commands on a linux based system.

**Hint:** the VM is only reachable from your host. You should not allow outside access since the VM is not hardend. This is a local playground and should not be allowed to be accessed via the network.

## Cleanup
To destroy it once you no longer need it via

```
vagrant destroy
```

---

## Customize the VM specs

You can alter the default configuration for the Vagrant VM in the top section of the Vagrantfile

```ruby
#########################
$CPU = 2
$MEMORY = 2048
$CPUEXECUTIONCAP = 50 # does not work with hyper-v
$IP = "192.168.0.4"   # does not work with hyper-v
$BASEOS = "centos/7"  
$SSH=2224
#########################
```