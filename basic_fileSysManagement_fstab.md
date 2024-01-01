#       File Systems Management

* Ways to list disks:
   > - `lsblk -f`
   > - `lsblk` (trimmed info)
   > - `blkid`
   > - `ls -l /dev/disk/by-uuid/`
   > - `ls -l /dev/disk/by-label/`
   > - see others in `ls -l /dev/disk/...`

* A good basic guide to get disk UUIDs

  > <https://linuxhandbook.com/get-uuid-disk/>

## fstab

* The fstab file contains a configuration table and rules for
  mounting file systems.
   > `/etc/fstab`
   
* Basic fstab file info

   > <https://www.redhat.com/sysadmin/etc-fstab>

* Files systems can be mounted via UUIDs or Lables.
  - we can choose either case (UUIDs recommended)
  - in either case we can designate the name of by creating a folder
    in `/mnt`, this will be the *mount point* (2nd column in `fstab`
    table), and pointing the *partition/device* to it (1st column
    in `fstab` table).
  - some info on UUIDs and Lables for mounting:
    
      > <https://linuxconfig.org/configure-systems-to-mount-file-systems-at-boot-by-universally-unique-id-uuid-or-label-rhcsa-objective-preparation> 

## gnome-disk-utility

* Petty much all the `fstab` info and options can be set/edited in
  the *gnome-disk-utility* (AKA *Disks*)...

