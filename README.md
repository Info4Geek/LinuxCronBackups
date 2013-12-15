LinuxCronBackups
================

Automated simple backup script for Linux.
MySQL backup included and FTP transfer.
Backups are therefore on hard disk and on remote FTP server.


Before start script you must do this:
-------------------------

1 - Open a terminal or connect with SSH to your server


2 - Install requiered paquets (rsync ncftp crontab):

	Debian, Ubuntu, ... : apt-get install rsync ncftp crontab

	Fedora: yum install rsync ncftp crontab

	OpenSUSE: zypper install rsync ncftp crontab

	ArchLinux: pacman -S rsync ncftp crontab

	Other: Google > "distribution_name install paquet"
	

3 - Create save folders:

```mkdir /var/backup && mkdir /var/backup/rsync && mkdir /var/backup/final```


4 - Edit following lines in the script with your needs:

```mysqldump >> --password=MySQLRootPassword```

```rsync >> /folder/do/you/want/to/backup/```

```
ncftpput >> -u username
			-p password
			serveradress
			"/remote/repertory"
```

You can also edit the default working folder. 
On my script default working folder is /var/backup


5 - You can add other rsync lines if you want to backup more folders and files


6 - Make the script executable:

Command: ```chmod +x /location/of/bacup_script```


7 - Cron your script for backups occur automatically when you want.

Command: ```crontab -e```

Add on the end of the file this:

```0 5 * * * bash /location/of/bacup_script```

In this case the backup will every day at 5am, you can change the time when baccup occur with your needs following the functioning of Cron.
Cron on Wikipedia: https://en.wikipedia.org/wiki/Crontab#Predefined_scheduling_definitions

Save the crontab file.


Start manualy backup script:
-------------------------
Go on the folder where the script is placed and start script.

Command: ```./bacup_script```
