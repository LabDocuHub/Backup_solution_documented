Current setup is wasting valuable space
It has space that could be allowing for drive image backups
It currently has overallocated space (2 TB) for VMs

The intention is to allocate 1300 GB for VM topologies on partition (V:), Disk 0, and 
560 GB for drive image backups on partition (B:) on Disk 0, similarly  

The second intention is to pick a drive image backup utility and implement it. 
The intention is to backup the C drive (OS partition) and the V drive (virtual machines partition) onto the B partion (drive image backup) located on the same drive as the VMs. This has disadvantages such as no protection for malware, ransomeware, fire, or theft, but does allow me to go back if something goes unexpected with my virtual drive setup or I want to restore windows after a bug or bad update.
