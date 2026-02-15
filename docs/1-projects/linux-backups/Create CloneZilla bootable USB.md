[[Linux]]
[[backups]]


To back up Ubuntu with Clonezilla, first create a bootable Clonezilla USB drive. Boot your computer from the USB, then select the "device-image" option and choose your local device (the external hard drive) as the destination. Next, select the source disk containing your system and start the backup process. 

1. Download [Clonezilla](https://clonezilla.org/downloads/download.php?branch=stable) ISO from the website.
2. Insert your USB drive
3. Identify your USB device name 
	1. Use the `lsblk` or `sudo fdisk -l` commands to identify your device name (e.g. `/dev/sdX*`). Selection the wrong device can lead to data loss! 


```bash
lsblk
```

- `lsblk`: List block devices information
	   ![[clonezilla_lsblk.png]]
	   ```bash
	     $ sudo fdisk -l | grep -i dev
	     ```
	- `fdisk` = create and manipulate partition tables. Block devices can be divided one or more logical disks called partitions. 
 `-l` = list the partition tables for a device
		![[clonezilla_fdisk_device_name.png]]
5. Unmount the USB drive
   ```bash
   df -h
   sudo umount /dev/SDX*
   ```
   - `df` = displays the amount of space on the file system
   - `umount` = detach a file system
	![[clonezilla_umount.png]]
5. Write the ISO to the USB drive using dd. Once completed you can boot from the USB. 
   ```bash
   sudo dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/dev/sdc1 status=progress bs=4M && sync
   ```
	   - dd - convert and copy a file
	   - if = $INPUT_PATH: specify the input file (your ISO)
	   - of = $OUTPUT_PATH: specify the output file (your USB device)
	   - bs=4M: sets the block size to 4 MB for faster write
	   - && sync: writes cached data to the disk before exit
6. Verify the ISO burned correctly by comparing the hashes of the file on disk and the USB:
   ```bash
   sha256sum clonezilla-live-3.3.0-33-amd64.iso
   sudo head -c $(stat -c %s clonezilla-live-3.3.0-33-amd64.iso) /dev/sdc1 | sha256sum
   ```
    - **`head`**: outputs the first part of files.
    - **`"-c" <size>`**: This option tells `head` to output only the first `<size>` bytes of the input. The `<size>` placeholder is replaced by the exact size (in bytes) of the original ISO file. This is the crucial part that ensures only the relevant data (the image itself, not any potential extra data or padding on the USB drive) is read for the checksum calculation.
    - **`/dev/sdX`**: This is the device path for your USB drive .
    - **`sha256sum`**: Calculates and outputs the SHA256 cryptographic hash (checksum) of the data it receives through standard input
      ![[clonezilla_checksum.png]]
7. If the checksums match, then eject the USB
   ```bash
   sudo eject /dev/sdX*
   ```
8. Boot your computer from the USB, then select the "device-image" option and choose your local device (the external hard drive) as the destination. Next, select the source disk containing your system and start the backup process. 
   

```bash
df -h
 1949  pwd`
 1950  dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/media/linux-joe/78E0-F73B/ status=PROGESS
 1951  man dd
 1952  dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/media/linux-joe/78E0-F73B/ status=progress
 1953  dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/media/linux-joe/78E0-F73B status=progress
 1954  ls /media/linux-joe/
 1955  ls /media/linux-joe/78E0-F73B/
 1956  df -h
 1957  lsblk
 1958  fdisk -l
 1959  sudo fdisk -l
 1960  dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/dev/sda1 status=progress
 1961  sudo dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/dev/sda1 status=progress
 1962  df -h
 1963  ls /dev/sda1
 1964  man dd
 1965  mount
 1966  sudo umount /dev/sda1
 1967  ls -lhart clonezilla-live-3.3.0-33-amd64.iso 
 1968  ls -lhart /media/linux-joe/3.3.0-33-amd64/
 1969  lsblk
 1970  sudo umount /dev/sda1
 1971  lsof +f -- /dev/sda1
 1972  kill -9 118270
 1973  lsof +f -- /def/sda/1
 1974  lsof +f -- /def/sda1
 1975  lsof +f -- /dev/sda1
 1976  sudo umount /dev/sda1
 1977  lsblk
 1978  df -h
 1979  sudo dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/dev/sda1 status=progress
 1980  sudo dd if=/home/linux-joe/Downloads/clonezilla-live-3.3.0-33-amd64.iso of=/dev/sda1 status=progress bs=4M && sync
 1981  ls 
 1982  df -h
 1983  lsblk
 1984  sudo umount /dev/sda1
 1985  lsblk
 1986  stat -c %s clonezilla-live-3.3.0-33-amd64.iso 
 1987  stat -c %s /dev/sda1
 1988  stat -c-n %s /dev/sda1
 1989  stat -c -n %s /dev/sda1
 1990  cmp -n $(stat -c %s clonezilla-live-3.3.0-33-amd64.iso) clonezilla-live-3.3.0-33-amd64.iso /dev/sda1
 1991  sudo cmp -n $(stat -c %s clonezilla-live-3.3.0-33-amd64.iso) clonezilla-live-3.3.0-33-amd64.iso /dev/sda1
 1992  sha256sum clonezilla-live-3.3.0-33-amd64.iso 
 1993  sudo head -c $(stat -c %s clonezilla-live-3.3.0-33-amd64.iso) /dev/sda1 | sha256sum 
 1994  sudo head -c $(stat -c %s clonezilla-live-3.3.0-33-amd64.iso) /dev/sda1
 1995  man stat
 1996  stat clonezilla-live-3.3.0-33-amd64.iso 
 1997  man stat
 1998  df -h
```

