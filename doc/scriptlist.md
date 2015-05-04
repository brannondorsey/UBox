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
Script for doing some initialization tasks for the UBox framework. Can run do the following tasks:
    - init  => Do initialization including hooks, part2 and modules
    - part2 => Creates folder, symlinks & sets permissions. 
    - modules => Enables the default modules configured in $PIRATEBOX_FOLDER/conf/default_modules.conf  .
    - imageboard =>  Configures kareha imageboard with basic configuration.
    - pyForum => Installs small Python forum
    - station_cnt => Installs crontab entry to export the number of connected clients to $PIRATEBOX_FOLDER/www/station_cnt.txt
    - flush_dns_reg => Installs crontab entry for regular dns cache refreshing
    - hostname => Changes hostname in some configuration & HTML files.  
	**Note**: Script needs rename, modularization (imageboard+pyForum), verify used configuration files.
- **json_generation.sh**
    - Generates JSON File about the configuration (enabled features and version). Currently uses:
        - DROOPY_ENABLED
        - DROOPY_PORT
        - HOST  
	**Note**: First concept, 'work in progress'.  
- **shoutbox_daemon.sh**  
	Launches a small daemon, which collects messages send across the network and posts it to the local shoutbox file. (Python)  
	**Note**: Beta, rarely tested.
- **station_cnt.sh** 
	Script that runs inside a cron that generates $PIRATEBOX_FOLDER/www/station_cnt.txt including the number of connected clients (via wifi).   
- **timesave.sh**
	Script to install & execute the timesave functionality. The purpose is to save the current date & time to a file, which is used to restore the date & time on a system without RTC on bootup.  

## Hooks  
Hooks are nearly empty files, that a called statically during specific points in initialization. These files are scripts that should be used by modder to include their custom initialization without the need of forking & overwriting the stock scripts. For including new functions during start & stop, please use the new module system.  
All hook files can be found in src/core/bin/hooks  
- **hook_pre_init.sh**  
This script is executed before any initialization is done. This can be used to change configuration dynamically, which can't be shipped statically- mostly to influence the default installation behaviour.  
- **hook_pre_openwrt_init.sh**  
This particular hook is for OpenWrt and is calles before the install_piratebox.sh script is called. It can be used to reconfigure OpenWrt specific things or based upon OpenWrt system calls the other configuration dynamicall, which can't be brought into place via static configuration files.  
- **hook_post_init.sh**  
This script is executed after the initialization took place. On this part folders and permissions are already at the final configuration. Place additional (re)configuration steps here.
