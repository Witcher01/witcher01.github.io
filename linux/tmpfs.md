# tmpfs

## Description
[tmpfs](https://wiki.archlinux.org/index.php/tmpfs) is a temporary filesystem on linux that purely resides in RAM. It can be used to significantly speed up file access or reduce read/write operations on a hard drive.
Arch Linux by default has `/tmp` mounted as a tmpfs.

## Usage
To mount a tmpfs, consult the manual page *tmpfs(5)*. Some simple things are:
- `mount -t tmpfs -o size=10M tmpfs /mnt/mytmpfs`

Since tmpfs is mounted via selecting a type from mount, all mount options apply. See *mount(8)*.
