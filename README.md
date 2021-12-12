# Archiving_and_Logging_Data
Assuming the role of a security analyst for the fictional company 'Credico Inc' to archive and log data

# Step 1: Create, Extract, Compress, and Manage tar Backup Archives

1. Command to extract the TarDocs.tar archive to the current directory:

**sudo tar xvvf TardDocs.tar**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2ac757055a1c93e8cece1a0794b2ddb0588c6f8f/Images/step%201%201.jpg)

2. Command to create the Javaless_Doc.tar archive from the TarDocs/ directory, while excluding the TarDocs/Documents/Java directory:

**Tar -cvf Javaless_Doc.tar --exclude=”TarDocs/Documents/Java” TarDocs/**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/step%201%202.jpg)

3. Command to ensure Java/ is not in the new Javaless_Docs.tar archive: 

**sudo tar tf Javaless_Doc.tar | grep "Java"**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/0c00015d3f4fb244f584be1c45cbf133b89e9f94/Images/step%201%203.jpg)

**Critical Analysis Question**

Why wouldn't you use the options -x and -c at the same time with tar?

X means to extract and c means to create. X would be used to extract data, like untar, while c would be used to create an archive. These two options within a command would cancel each other out and the command would not work. Once the tar is created it would just extract everything, making the command pointless.

# Step 2: Create, Manage, and Automate Cron Jobs

1. Cron job for backing up the /var/log/auth.log file:

**0 6 * * 3 tar cvfz ~/Documents/Projects/auth_backup.tar.gz var/log/auth.log**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/Step%202%201.jpg)

# Step 3: Write Basic Bash Scripts

1. Brace expansion command to create the four subdirectories:

**sudo mkdir ~/backups/{freemem,diskuse,openlist,freedisk}**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/step%203%201.jpg)

*I later noticed the spelling mistake for ‘freedisk’ and renamed the directory*

Paste your system.sh script edits below:

2. #!/bin/bash

**free -lh > ~/backups/freemem/free_mem.txt**

**df -h > ~/backups/diskuse/disk_usage.txt**

**lsof > ~/backups/openlist/open_list.txt**

**df -h / > ~/backups/freedisk/free_disk.txt**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/step%203%202.jpg)

3. Command to make the system.sh script executable: 

**chmod 744 system.sh**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/step%203%203.jpg)

**Optional**

1. Commands to test the script and confirm its execution: 

**sudo ./system.sh**

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/optional.jpg)

# Step 4. Manage Log File Sizes

1. Run sudo nano /etc/logrotate.conf to edit the logrotate configuration file.

Configure a log rotation scheme that backs up authentication messages to the /var/log/auth.log.

- Add your config file edits below:

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/e023b60543625a050d1359611f1be8883db443a8/Images/config%20file%20var.png)

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/step%204a.jpg)

![name-of-you-image](https://github.com/ldover29/Archiving_and_Logging_Data/blob/2edf9ef2e62fb2d623abfad43ca5ba4ade85228c/Images/step%204b.png)

