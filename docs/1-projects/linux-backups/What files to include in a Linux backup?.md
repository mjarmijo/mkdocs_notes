[[Linux]]
[[backups]]

When backing up a Linux system to a NAS, the most critical files to include are user data, system configurations, and locally installed software. A common strategy is to back up essential directories while excluding temporary or non-essential system files to save space and time. [1, 2, 3, 4, 5]  
Essential Directories to Include 

• /home/: This is where all user data, personal documents, downloads, and user-specific configurations are stored. Backing this up is critical. 
• /etc/: Contains all system-wide configuration files, network settings, and service configurations. This is crucial for restoring your system setup. 
• /var/: Contains variable data, including logs, databases, mail, and application data. Key subdirectories to consider are: 

	• : For local mail storage. 
	• : If you host web content here. 
	• : This directory often contains automatically generated package lists and other useful recovery data. 
	• : Contains variable state data for applications; review subdirectories to decide what is necessary. 

• /root/: The home directory for the root user, which may contain important administrative scripts and configurations. 
• /usr/local/: Used for storing locally compiled or hand-installed software and scripts not managed by the system's package manager. 
• /opt/ and /srv/: These directories may contain optional application data or service-specific files. Back up these if you have stored anything here. [1, 2, 6, 7, 8]  

Directories to Exclude [2]  
Generally, you should exclude directories that contain temporary data, caches, or easily reinstallable system binaries, as including them can make backups unnecessarily large and slow. 

• /dev/: Contains device files, which are dynamically created and not needed in a backup. 
• /proc/ and /sys/: Virtual filesystems that contain real-time kernel and process information, not persistent data. 
• /tmp/ and /var/tmp/: Temporary scratch spaces that are cleared periodically. 
• /run/ and /var/run/: Contains data relevant only to the current running system. 
• /mnt/ and /media/: These are typically mount points for other drives or network shares. Backing up their contents (which are usually backed up from their original source) can lead to redundant backups or infinite loops. 
• /boot/: While important, the configuration files within  and a list of installed packages are often sufficient for recovery. The kernel and initramfs images themselves can usually be reinstalled via a package manager. [1, 14, 15, 16, 17]  

Backup Tools and Strategy 
You can use various tools to perform these backups to a NAS, often mounting the NAS share using protocols like SMB or NFS. 

• Rsync: A powerful command-line tool for efficient incremental backups that only copies changed files. 
• GUI Tools: Options like Back In Time or Deja Dup offer a user-friendly interface for setting up include/exclude rules. 
• Best Practice: Employ the 3-2-1 backup rule: keep three copies of data, on two different types of media, with one copy stored off-site. Your NAS can serve as one of the local media types. [9, 14, 19, 20, 21]  

AI responses may include mistakes.

[1] https://unix.stackexchange.com/questions/1067/what-directories-do-i-need-to-back-up
[2] https://www.zmanda.com/blog/how-to-backup-linux-directories-and-files/
[3] https://www.zmanda.com/blog/linux-backup-a-guide-for-system-administrators/
[4] https://www.acronis.com/en/solutions/backup/physical/linux/
[5] https://www.itjones.com/blogs/2018/12/best-nas-network-attached-storage
[6] https://tanav2202.medium.com/linux-filesystem-and-user-permissions-62072db8df89
[7] https://tonylixu.medium.com/devops-in-linux-var-6a22c8df65e8
[8] https://medium.com/@ridwaneelfilali/linux-directory-hierarchy-2e7c6da8a151
[9] https://www.youtube.com/watch?v=lR9OvVb5RvI
[10] https://www.linode.com/docs/guides/backing-up-your-data/
[11] https://www.interserver.net/tips/kb/shared-hosting-and-backups/
[12] https://www.truenas.com/docs/scale/scaleuireference/dataprotection/truecloudbackuptasksscreen/
[13] https://blog.devops.dev/restic-backups-protect-your-server-before-disaster-strikes-9f76eb16a711
[14] https://askubuntu.com/questions/222326/which-folders-to-include-in-backup
[15] https://forums.opensuse.org/t/use-smb-cifs-nas-for-backing-up-linux/143390
[16] https://www.zmanda.com/blog/how-to-backup-linux-directories-and-files/
[17] https://betterstack.com/community/questions/what-directories-on-linux-should-be-in-a-server-backup/
[18] https://www.rubrik.com/insights/nas-backup-guide-for-organizations-a-comprehensive-resource
[19] https://kb.synology.com/DSM/tutorial/How_to_back_up_Linux_computer_to_Synology_NAS
[20] https://www.commvault.com/explore/nas-backup
[21] https://www.tecmint.com/linux-system-backup-tools/

