Using Diskpart in Command Prompt is a reliable way to execute partitioning Disk 0 without running into "unmovable file" limitations often hit in the graphical Disk Management tool.

Here is the step-by-step procedure to shrink your V: drive and create partition B:
Open an Elevated Command Prompt: Press the Windows Key, type cmd, right-click on Command Prompt, and select Run as administrator.
   Launch Diskpart: Type diskpart and press Enter.
   Locate your 2 TB SSD: Type list disk and press Enter. Look for the disk number that is roughly 1,863 GB (this is your physical 2 TB drive).
   Select the Disk: Type select disk X (replace X with your 2 TB disk number, in this case, disk 0 and press Enter.
   Locate the VM Partition: Type list partition or list volume and press Enter to identify your V: drive partition.
   Select the VM Partition: Type select volume V (or select the partition number using select partition Y) and press Enter.
   Shrink the Volume: Since you want the drive to end up at exactly 1,300 GB, you need to shrink it by roughly 560 GB.
   Type the following command to shrink it by exactly 560 GB (573,440 MB) and press Enter:

shrink desired=573440

Create the New Backup Partition:
    Once the shrink completes successfully, create the new partition out of the unallocated space by typing the following command and pressing Enter:
    
create partition primary

Format the New Partition:
Format the new space as an NTFS file system and give it a quick format by typing the following command and pressing Enter:
    
format fs=ntfs quick label="Drive Image Backups"

Assign Drive Letter B: Assign the explicit letter B by typing the following command and pressing Enter:
 
assign letter=B

Exit Diskpart: Type exit and press Enter to close out the utility.
    
Your 2 TB drive will now be flawlessly split into a 1,300 GB V: drive for your dynamic virtual hard disks and a 560 GB B: drive dedicated to your system recovery images.

The volume has been safely prepared. To finish setting up your drive, let's create, format, and assign the new B: drive partition from the space you just freed up.
Type these commands into your prompt one at a time, pressing Enter after each one:
Create the new backup partition:
   
create partition primary

Format the partition cleanly as NTFS (using a minimal, clean label):

format fs=ntfs quick label="SysBackup"

Assign the drive letter B:

assign letter=B

Exit the utility:

exit


Configuration Layer	Action Item for Internal SSD Backups  

The "All-Egg" Risk	An internal backup protects against a C: drive failure or a bad software update, but it does not protect against power surges, physical theft, fire, or ransomware that targets all attached internal drives.  

Separating VM Backups	If you are backing up your virtual machines (V: drive) to your backup drive (B: drive), make sure the VMs are shut down or suspended when Hasleo runs to prevent the virtual disks from corrupting during a live image capture.  

Emergency Rescue Media	Keep a bootable Hasleo WinPE USB flash drive handy. If your main drive fails, you will need to boot to that USB to pull the backup images from your second internal SSD and push them back onto your main drive.  
