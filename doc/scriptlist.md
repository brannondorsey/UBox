# scriptlist.md
**Description:** list including descriptions of available scripts.  
**Author:** Mathias Strubel, Stijn van de Ridder.  
**Location:** /doc/scriptlist.md  

## src/core/bin 
- **avahi_to_sdns.sh**    
	Reads piratebox.conf and polls avahi-browse infinite. It stores the results in the host_mesh file, when done with generating dnsmasq gets a SIGHUB from flush_dnsmasq.sh and refreshes its caches.  
- **board-autoconf.sh**  
	This script generates a random secret for the imageboard and asks the user for ADMIN_PASS and sets this in the configuration file.  
	**Note**: uses static paths.
- **delete_empty.sh**  
	This script scans the folder given as first parameter for empty files and deletes them.  
- **distribute_files.sh**  
	This script is used to distribute files into (sub-)directories, can be switched to debug mode if exported environment variable DEBUG=true.  
	**Note**: uses distribute_file_into_directory.sh
- **droopy**  
	This is a python 2 upload script.  
	**Note**: not IPv6 compatible.
- **exchange_www.sh**    
	This is a script for moving the www directory to an USB stick.  
	**Note**: obsolete.
- **find_interface_name.sh**  
		This is the module for the new modulized startup. It is mainly used for scripts that rely on (hardcoded or generated) interface names. This script parses bridge.conf, network.conf and hostap.conf and tries to find the first configured interface.  
	**Note**: the script calls itself recursively.
- **flush_dnsmasq.sh**  
	This is a script to send a SIGHUB to dnsmasq.  
	**Note**: outdated and needs a rework.
- **install_piratebox.sh**  
- **json_generation.sh**  
- **shoutbox_daemon.sh**  
- **station_cnt.sh**  
- **timesave.sh**  
## Hooks  
- **hook_pre_init.sh**  
- **hook_pre_openwrt_init.sh**  
- **hook_post_init.sh**  

