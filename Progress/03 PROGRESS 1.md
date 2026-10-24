Using Diskpart in Command Prompt is a reliable way to execute partitioning Disk 0 without running into "unmovable file" limitations often hit in the graphical Disk Management tool.  

Here is the step-by-step procedure to shrink the V: drive and create partition B:  
Open an Elevated Command Prompt:   

   Launch Diskpart: Type 'diskpart' and press Enter. 
   
   Locate my 2 TB SSD (disk 0): Type 'list disk' and press Enter. Look for the disk number that is roughly 1,863 GB (this is my physical 2 TB drive).   
   
   Select the Disk: Type 'select disk 0' and press Enter.  
   
   Locate the virtual machine Partition: Type 'list partition' and press Enter to identify my V: drive partition.
   Select the VM Partition: 
   
   Type 'select volume 0' and press Enter.  
   
   Shrink the Volume: Since you want the drive to end up at exactly 1,300 GB, you need to shrink it by roughly 560 GB.
   Type the following command to shrink it by exactly 560 GB (573,440 MB) and press Enter:

'shrink desired=573440'

I create the New Backup Partition:
    Once the shrink completes successfully, I create the new partition out of the unallocated space by typing the following command and pressing Enter:
    
'create partition primary'

Format the New Partition:  

Format the new space as an NTFS file system and give it a quick format by typing the following command and pressing Enter:
    
'format fs=ntfs quick label="Drive Image Backups"'

Assign Drive Letter B: Assign the explicit letter B by typing the following command and pressing Enter:
 
'assign letter=B'

Exit Diskpart: Type 'exit' and press Enter to close out the utility.
    
My 2 TB drive is now split into a 1,303 GB V:\ drive for dynamic virtual hard disks and a 560 GB B:\ drive dedicated to my system recovery images.

The volume has been safely prepared. To finish setting up my drive, I create, format, and assign the new B:\ drive partition from the space I just freed up.  

Type these commands into my prompt one at a time, pressing Enter after each one. Create the new backup partition:
   
'create partition primary'

Format the partition cleanly as NTFS (using a minimal, clean label):

'format fs=ntfs quick label="SysBackup"'

Assign the drive letter B:

'assign letter=B'

Exit the utility:

'exit'

