
# QEMU/KVM

> *from Veronica Explains*

>>*QEMU/KVM for absolute beginners*

>>*<https://www.youtube.com/watch?v=BgZHbCDFODk>*

##       Kernel Based Virtual Machine 

* QEMU, or Quick Emulator, is a FOSS processor emulator.

* KVMs are hypervisors let you run complete isolated operating<br>
  systems inside your PC 
  - KVM is baked in Linux
  - GREAT for cloning VMs, backup and restore

## Getting Started
* Checking if virtualisation is possible
   > `egrep -c '(vmx|svm)' /proc/cpuinfo`

  - "vmx" is for intel and "svm" is for AMD
  - Returns count of cpus with virtualisation 
    enabled
     * You are good as long as its more than zero... 

### What We Need
1. qwmu-kvm: the package of emulator itself
2. libvirt-daemon: runs virtualisation in background
    - *daemon: a program that runs in the background* 
3. bridge-utils: vital for networking VM to network
4. virt-manager: graphical program used to manage VMs

* Packages can vary a bit distro to distro but these are what we need:

    > - `sudo apt install qemu-kvm libvirt-daemon-system`
    > - `sudo apt install libvirt-clients bridge-utils virt-manager`
    > - `sudo apt install virt-manager`

# Setup 

* Start libvirt daemon
   > `sudo systemctl start libvirtd`

* Start libvirt daemon on startup
   > `sudo systemctl enable libvirtd`

* virsh: For cli kvm startup (see virsh -h)...
  - We won't be using this in the setup BUT `virsh` becomes necessary<br>
    when debugging and fixing issues.
  - In fact a common bug is when VMs can't launch with the bug saying<br>
    "network 'default' is not active" (can happen after host restart)
     * This shows what the problem is:
         - `sudo virsh net-list --all`
     * This solves the bug:
         - `sudo virsh net-start default`
         - possible permanent fix:
              - `sudo virsh net-autostart --network default`
     * Some sites for this particular bug
         - <https://forums.opensuse.org/t/qemu-kvm-requested-operation-is-not-valid-network-default-is-not-active/149814>
         - <https://askubuntu.com/questions/1036297/cant-start-kvm-guest-network-default-is-not-active>
         - <https://www.reddit.com/r/VFIO/comments/6iwth1/network_default_is_not_active_after_every/>
     * *We don't need to worry about this bug or virsh now*
         - *deal with bug if/when it shows up*
         - *use virsh if/when necessary*

## Virt Manager (Virtual Machine Manager)
* Create an image pool: just a dir with ISOs...
  - Click browse and click "+" lower left to "add pool"
    * Name the "pool" and select a dir for ISO(s)... 
  - Create a storage "pool" for KVM storage file
    * Name the "pool" and select a dir for storage file(s)

* The KVM must have permissions to accesses to storage file
  - Enable as necessary:
     > * `sudo adduser USERNAME libvirt` 
     > * `sudo adduser USERNAME libvirt-qemu`

  - See the site below to debug access/permissions issues with KVM
     * <https://ostechnix.com/solved-cannot-access-storage-file-permission-denied-error-in-kvm-libvirt/>

  - Another solution to permissions issues is using `chmod`
     > Give rwx access to GROUP ( may require EVERYONE access...)

### A *Working* Setup (in LMDE6)
* Applied a mixture of solutions from site above...
  > The qemu config file: `sudo vim /etc/libvirt/qemu.conf`

        #
        #user = "libvirt-qemu">
        user = "USERNAME"
        user = "libvirt-qemu"

        # The group for QEMU processes run by the system instance. It can be
        # specified in a similar way to user
        #group = "libvirt-qemu"
        group = "libvirt-qemu"

* In some cases the user & group names are "libvirt-qemu" (LMDE6), in<br>
  other cases it may be "libvirt" (typically) or something like that...

## Shared KVM Folder with Host
* Click 'Add Hardware" (bottom left) in virt manager and select<br>
  `Filesystem` in left menu.
   - Leave the driver as `virtiofs` (this is the setup/FileSystem<br>
     used in this guide)
   - Select a `Source path` from host system to share
   - Set a `Target path`
      * Basically a `tag` for the guest to recognize as a device that<br>
        is mountable in `fstab` 
   - Must enable shared memory (memory settings in virt manager)

* Create a dedicated share DIR in `/mnt` of guest. This folder must be<br>
  mounted every time KVM starts up

  - > `sudo mount -t virtiofs tag /mnt/shareDIR`

     * The `tag` is set in hardware file share setup (above)
     * The `/mnt/shareDIR` is the share folder in guest (KVM)

  - For automatic mount at KVM startup edit the KVM `fstab`

     - > `sudo vim /etc/fstap`

     - > add line: `'tag'` `'guest_dir'` `virtiofs` `defaults` `0` `0`

         - `tag`(device) `guest_dir`(mountPoint) `virtiofs`(fileSystemType) `defaults`(options) `0` `0`
         -  for `fstab` details see: <https://www.redhat.com/sysadmin/etc-fstab>

* The KVM **MUST** have access/permissions to shared folder
  or it can't "mount" in KVM
  - In this case we applied total permissions, AKA "everything for
    everyone" (chmod 777)

   > `sudo chmod -R 777 sharedDIR`
   >> * `-R` is for all sub dirs recursive
   >> * Although, `{rwxr--r--}` should be enough
   >>   - You can always change back or to something else with `chmod`
   >>     * Just make sure it's recursive (`-R`)

* A link for chmod command:
  * <https://linuxhandbook.com/chmod-command/>

* See links for setup & debug of shared folders for KVMs:
  * <https://www.debugpoint.com/share-folder-virt-manager/>
  * <https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/>
  * Share folder setup for windows
     - <https://www.debugpoint.com/kvm-share-folder-windows-guest/> 
