![Maintenance](https://img.shields.io/maintenance/yes/2019)
![GitHub](https://img.shields.io/github/license/gepardec/vagrant-docker)
<p align="right">
<img alt="gepardec" width=100px src="https://github.com/Gepardec/vagrant-docker/raw/master/.images/gepardec.png">
</p>
<br>
<br>

# vagrant-docker

We love to docker. To get started with docker is easy. Almost any OS for your workstation now supports docker. Just install it and you can get started. But for a training / test environment it is best if everybody uses the same setup. The goal is to have a common environment in which we can work and fix errors if they occur, not one per participant. This is why we have put docker into a CentOS 7 based VM that can easily be used via vagrant.

## Preflight

You can run our docker training environment on your workstation once you have 

* [Vagrant](https://www.vagrantup.com/intro/getting-started/install.html)
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

installed and downloaded this git repo. 


## Quickstart

To bootstrap the CentOS 7 VM with docker simply run.

```
vagrant up
```

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
$CPUEXECUTIONCAP = 50
$IP = "192.168.0.3"
$BASEOS = "centos/7"
$SSH=2224
#########################
```