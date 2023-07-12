Uses a single file tree, while windows uses seperate trees of files at each location (mounts attached partitions at new locations)
- Ex : Windows - C:, D:, E:, Linux - Single parititon

Storage and loops exist as files in /dev/

**Hierarchy
Linux is IAW file system heirarchy standard (FHS)
- Windows tends to group files per application, FHS groups files by type

Not all distros FS are the same. However all start with the root directory "/"

**Binary directories** 
/sbin - critical binaries for bootnig and low level system maintenance
/bin - common binares required to be availabkle to all users and root
/usr/bin - binaries availbale to any locally logged in user

**Other directories**
/opt optional software
/etc - system config files, conf files ususally named after the program
/home - user home directories
/media - removable media, default location but can be mounted anywhere
/tmp - temp folders, cleaned on restart, **good starting point for hackers**



**Commands**
df
lsblk
fdisk - l
man hier 

Mount insertable media
mkdir /tmp/mnt
lsblk
sudo mount /dev/sr0 /tmp/mnt

Mount file
mkdir /tmp/mnt
sudo mount file.iso /tmp/mnt


