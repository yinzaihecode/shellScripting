## 중요 | 관리자 권한으로 실행. | 

```powershell
dism.exe /Online /Disable-Feature:Microsoft-Hyper-V-All
bcdedit /set hypervisorlaunchtype off
```



## cd setup
```
cd shellclass\textbox01
vagrant reload

```





## 1. vagrant add

```
vagrant box add jasonc/centos7
```
```
C:\Users\jay>vagrant box add jasonc/centos7
==> box: Loading metadata for box 'jasonc/centos7'
    box: URL: https://vagrantcloud.com/jasonc/centos7
==> box: Adding box 'jasonc/centos7' (v1.4.4) for provider: virtualbox
    box: Downloading: https://vagrantcloud.com/jasonc/boxes/centos7/versions/1.4.4/providers/virtualbox.box
Download redirected to host: vagrantcloud-files-production.s3.amazonaws.com
    box:
==> box: Successfully added box 'jasonc/centos7' (v1.4.4) for 'virtualbox'!
```


## 2. MKDIR shellclass, testbox01
---

```powershell
C:\Users\jay\shellclass\textbox01>vagrant init jasonc/centos7
# <!-- 이미 VM이 있는 경우, virtual Box. -->
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```


<!-- C:\Users\jay>cd shellclass\textbox01 -->



## 2-1. vagrant up.
---
```powershell
C:\Users\jay\shellclass\textbox01>vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'jasonc/centos7'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'jasonc/centos7' version '1.4.4' is up to date...
==> default: Setting the name of the VM: textbox01_default_1614782400478_74232
Vagrant is currently configured to create VirtualBox synced folders with
the `SharedFoldersEnableSymlinksCreate` option enabled. If the Vagrant
guest is not trusted, you may want to disable this option. For more
information on this option, please refer to the VirtualBox manual:

  https://www.virtualbox.org/manual/ch04.html#sharedfolders

This option can be disabled globally with an environment variable:

  VAGRANT_DISABLE_VBOXSYMLINKCREATE=1

or on a per folder basis within the Vagrantfile:

  config.vm.synced_folder '/host/path', '/guest/path', SharedFoldersEnableSymlinksCreate: false
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
There was an error while executing `VBoxManage`, a CLI used by Vagrant
for controlling VirtualBox. The command and stderr is shown below.

Command: ["startvm", "2d93d459-2cee-4056-a421-5239d0d3f744", "--type", "headless"]

Stderr: VBoxManage.exe: error: VT-x is not available (VERR_VMX_NO_VMX)
VBoxManage.exe: error: Details: code E_FAIL (0x80004005), component ConsoleWrap, interface IConsole

C:\Users\jay\shellclass\textbox01>
```
<!-- vtx 설정 bios에서 조절해야함 -->
<!-- T/S 비디오 참고. -->

## 3. vagrant status
---

```powershell
C:\Users\jay\shellclass\textbox01>vagrant status
Current machine states:

default                   poweroff (virtualbox)

The VM is powered off. To restart the VM, simply run `vagrant up`
C:\Users\jay\shellclass\textbox01>
```

## 4. vagrant ssh
---
```powershell
C:\Users\jay\shellclass\textbox01>vagrant ssh
VM must be running to open SSH connection. Run `vagrant up`
to start the virtual machine.
```

## 5. vagrant halt
---
```powershell
vagrant halt
```

## 6. vagrant reload
---
```powershell
vagrant reload

```

## error | (VERR_VMX_NO_VMX)  | 

```powersehll
C:\Users\jay\shellclass\textbox01>vagrant reload
==> default: Checking if box 'jasonc/centos7' version '1.4.4' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
There was an error while executing `VBoxManage`, a CLI used by Vagrant
for controlling VirtualBox. The command and stderr is shown below.

Command: ["startvm", "2d93d459-2cee-4056-a421-5239d0d3f744", "--type", "headless"]

Stderr: VBoxManage.exe: error: VT-x is not available (VERR_VMX_NO_VMX)
VBoxManage.exe: error: Details: code E_FAIL (0x80004005), component ConsoleWrap, interface IConsole

C:\Users\jay\shellclass\textbox01>vagrant reload
> dism.exe /Online /Disable-Feature:Microsoft-Hyper-V
```

## OK  | Vagrant reload | 
```
C:\Users\jay\shellclass\textbox01>vagrant reload
==> default: Checking if box 'jasonc/centos7' version '1.4.4' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Setting hostname...
==> default: Mounting shared folders...
    default: /vagrant => C:/Users/jay/shellclass/textbox01
==> default: Machine already provisioned. Run `vagrant provision` or use the `--provision`
==> default: flag to force provisioning. Provisioners marked to run always will still run.
```


## Vagrant Destroy.

--- 

## new project

```
C:\Users\jay\shellclass>mkdir multitest
C:\Users\jay\shellclass>cd multitest
vagrant init jasonc/centos7

```


```
vagrant file을 다음과 같이 설정
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "jasonc/centos7"
  

  config.vm.define "test1" do |test1|
    test1.vm.hostname = "test1"
    test1.vm.network "private_network", ip: "10.9.8.5"
  end

  config.vm.define "test2" do |test2|
    test2.vm.hostname = "test2"
    test2.vm.network "private_network", ip: "10.9.8.6"
  end
```

# vagrant up
# vagrant status
```
C:\Users\jay\shellclass\multitest>vagrant status
Current machine states:

test1                     running (virtualbox)
test2                     running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```
# ssh connect | test1, test2|
```
C:\Users\jay\shellclass\multitest>vagrant ssh test1
[vagrant@test1 ~]$ exit
logout
Connection to 127.0.0.1 closed.

C:\Users\jay\shellclass\multitest>vagrant ssh test2
[vagrant@test2 ~]$ exit
logout
Connection to 127.0.0.1 closed.

```



# vagrant ssh test 1
























