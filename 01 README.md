# Step 1. Partitioning Secondary SSD  

Current setup is 1 TB SSD drive for host OS named disk 1.  
On the same motherboard is a secondary 2 TB SSD reserved for virtual machines named disk 0. 

Disk 1 is 931.50 GB contains the host (C:\ partition)
Disk 0 is 1863.00 GB (V:\ partition)

Disk 0 (secondary SSD) is set for 1863.00 GB NTFS and is initially reserved entirely for virtaul machine files only. 
<img width="934" height="592" alt="Screenshot 2026-10-19 190755" src="https://github.com/user-attachments/assets/378888e1-caf8-40d0-834f-42b3e4fe95fa" />
Command line (Admin) was used to shrink drive and add new partion. Partition V:\ (original partition) on disk 0 named 'VM_Storage' was shrunk to 1303.00 GB NTFS, and a new partition B:\ with remaining space was named 'Disk Image Backup' and set for 560.00 GB NTFS.
<img width="940" height="682" alt="Screenshot 2026-10-19 201154" src="https://github.com/user-attachments/assets/7112b5d9-0d52-4369-a82d-fd950de4e9d5" />  

This PC does not employ BitLocker encryption. If I do at some point there would be other considerations in using Hasleo Backup Suite Free V5.9.2.4.

Things I considered about internal SSD Backups  

The "All-Egg" Risk:	An internal backup protects against a C: drive failure or a bad software update. That is what I am getting. It does not protect against power surges, physical theft, fire, or ransomware that targets all attached internal drives.  

Separating VM Backups:	If you are backing up your virtual machines (V: drive) to your backup drive (B: drive), make sure the VMs are shut down or suspended when Hasleo runs to prevent the virtual disks from corrupting during a live image capture.  

Emergency Rescue Media:	Keep a bootable Hasleo WinPE USB flash drive handy. If your main drive fails, you will need to boot to that USB to pull the backup images from your second internal SSD and push them back onto your main drive. 

I decided to use what I got and backup to the B:\ partition.

I chose differential backups because they are more stable. 

*If last week's backup file gets corrupted or deleted, today's backup still works perfectly. I never lose my entire backup history because of one bad file.  
Restoration Errors	The recovery engine only has to stitch two files together: your baseline Full Backup and your chosen Differential snapshot. Fewer moving parts mean fewer opportunities for the software to glitch or mismatch during a critical system recovery.  
Data Integrity	Hasleo uses a built-in feature called VSS (Volume Shadow Copy) to capture the differential block changes. Because Windows pauses write operations cleanly for a fraction of a second, the data being written to Drive B is verified and structurally stable.* 
