# Vision for this project  

Current setup is wasting valuable space
It has space that could be allowing for drive image backups
It currently has overallocated space (2 TB) for VMs

The intention is to allocate 1300 GB for VM topologies on partition (V:), Disk 0, and 
560 GB for drive image backups on partition (B:) on Disk 0, similarly. Note, the Virtual Hard Disks path and the Checkpoint File Location path are both explicitly targeted to folders inside the 1,303 GB Drive V.

The second intention is to pick a drive image backup utility and implement it. 
The backup will include the C:\ drive (OS partition) and the V:\ drive (virtual machines partition) to be copied onto the B:\ drive partition (drive image backup). Both the C:\ and V:\ drive images will seperately be located on the same drive as the peripheral drive on the motherboard. This has disadvantages such as no protection for malware, ransomeware, fire, or theft, but does allow me to go back in time if something goes unexpected with my virtual drive setup or I want to restore windows after a bad install, a bug, or bad update.
