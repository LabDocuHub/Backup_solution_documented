# partitioning_drives_for_personal_computer  
Documenting a standard process for personal use and reference   

Current setup is 1 TB SSD for host OS  
2 TB SSD reserved for virtual machines on the same motherboard.  
Disk 1 is 931.50 GB  
Disk 0 is 1863.00 GB  
Host partition Disk 1 is 200 MB reserved for Healthy (EFI System)  
Host partion Disk 1 labeled 'C:' is set for 930.40 GB of NTFS  
Host partion Disk 1 labeled 'Healthy (Recovery Partition) is set for 918 MB  
VM partition Disk 0 is set for 1863.00 GB NTFS  
<img width="934" height="592" alt="Screenshot 2026-10-19 190755" src="https://github.com/user-attachments/assets/378888e1-caf8-40d0-834f-42b3e4fe95fa" />
Command line (Admin) was used to shrink and add new partion. Partition letter V (original partition) on disk 0 which was named 'VM_Storage' was shrunk and a new partition with remaining space named 'Disk Image Backup' was labeled drive 'B'.
<img width="940" height="682" alt="Screenshot 2026-10-19 201154" src="https://github.com/user-attachments/assets/7112b5d9-0d52-4369-a82d-fd950de4e9d5" />  

This PC does not employ BitLocker encryption. If I do at some point there would be other considerations in using Hasleo Backup Suite Free V5.9.2.4.
