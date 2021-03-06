# vm automate it.

---

## vagrant Boxes
## Box = Operating System Image

```
vagrant box add USER/BOX
```

### EX
```
vagrant box add jasonc/centos7
```

### Many PUblic boxes to download.


## Vagrant Projects = FOlder with a VagrantFile.

1. mkdir vm1
2. cd vm1
3. Now init the Vagrant Proejct:


# Vagrant up
**Vagrant will import the box into VirtualBox and start it.**

* The Vm is started in headless mode.
  * vagrant Up / Multi-Machine.
  * vagrant up master
  * vagrant up server1

---

# SSH - Secure Shell

```
vagrant ssh [VM-NAME]
exit
requires ssh client
<!-- git 설치 시에 자동으로 깔림ㅎ -->
```

|제목|내용|설명|
|:---|:---:|---:|
|좌로정렬|중앙정렬|우로정렬|






|command |to do|
|---:|:---:|
|vagrant halt [vm]|stops the vm|
|vagrant up [vm]|starts the vm|
|vagrant suspend [vm]|Suspends the vm|
|vagrant resume [vm]|resume the vm|
|vagrant destory [vm]|destory the vm|

## Vagrantfile

```sh
Vagrant.configure("2") do |config|
  config.vm.box = "jasonc/centos7"
  config.vm.hostname = "testbox01"
  config.vm.network "private_network", ip: "10.2.3.4"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "1024"
  end
end
```

## EX
```sh
Vagrant.configure("2") do |config|
  config.vm.box = "jasonc/centos7"

  config.vm.define "server1" do |server1|
    server1.vm.hostname= "server1"
    server1.vm.network "private_network", ip: "10.2.3.4"
  end

  config.vm.define "server2" do |server2|
    server1.vm.hostname= "server2"
    server1.vm.network "private_network", ip: "10.2.3.5"
  end
 end
  
```

















