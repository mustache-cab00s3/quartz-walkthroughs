## Setup
- Prerequisites
	- [Oracle VirtualBox](https://www.virtualbox.org/)
	- Favorite Testing platform 
		- https://www.kali.org/

1. Download the virtual machine from [Vulnhub.com](https://www.vulnhub.com/entry/shenron-1,630/)
	1. https://download.vulnhub.com/shenron/shenron-1.ova
	2. Import the VM into the Manager.
		1. File --> Import Appliance (Ctrl + i)
		2. select `shenron-1.ova` --> open
		3. Finish
	3. Ensure network configuration
		1. Machine --> Settings (Ctrl + s)
		2. Network section -- Adapter 1
			1. Enable Network Adapter
			2. Attached to (List of Adapters)
				1. Ensure Testing and Target machines are both on the same network
	4. Start VM
