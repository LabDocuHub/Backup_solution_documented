Using Diskpart in Command Prompt is a reliable way to execute partitioning Disk 0 without running into "unmovable file" limitations often hit in the graphical Disk Management tool.

Here is the step-by-step procedure to shrink your V: drive and create partition B:
1. Open an Elevated Command Prompt: Press the Windows Key, type cmd, right-click on Command Prompt, and select Run as administrator.
2. Launch Diskpart: Type diskpart and press Enter.
3. Locate your 2 TB SSD: Type list disk and press Enter. Look for the disk number that is roughly 1,863 GB (this is your physical 2 TB drive).
4. Select the Disk: Type select disk X (replace X with your 2 TB disk number, usually 1 if your system drive is 0) and press Enter.
5. Locate the VM Partition: Type list partition or list volume and press Enter to identify your V: drive partition.
6. Select the VM Partition: Type select volume V (or select the partition number using select partition Y) and press Enter.
7. Shrink the Volume: Since you want the drive to end up at exactly 1,300 GB, you need to shrink it by roughly 560 GB. Type the following command to shrink it by exactly 560 GB (573,440 MB) and press Enter:cmd
shrink desired=573440
Use code with caution.
8. Create the New Backup Partition: Once the shrink completes successfully, create the new partition out of the unallocated space by typing the following command and pressing Enter:cmd
create partition primary
Use code with caution.
9. Format the New Partition: Format the new space as an NTFS file system and give it a quick format by typing the following command and pressing Enter:cmd
format fs=ntfs quick label="Drive Image Backups"
Use code with caution.
10. Assign Drive Letter B: Assign the explicit letter B by typing the following command and pressing Enter:cmd
assign letter=B
Use code with caution.
11. Exit Diskpart: Type exit and press Enter to close out the utility.
Your 2 TB drive will now be flawlessly split into a 1,300 GB V: drive for your dynamic virtual hard disks and a 560 GB B: drive dedicated to your system recovery images.
