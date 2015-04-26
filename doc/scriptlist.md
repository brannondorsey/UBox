# List and description of available scripts#

## src/core/bin ##

  - **avahi_to_sdns.sh**
        Reads piratebox.conf ;
        This module pulls infinitive against avahi-browse and generates the results into the hosts_mesh file. After generating, dnsmasq gets a SIGHUB from that script to refresh its caches. That file is used from dnsmasq to resolve hostnames dynamically from "distant" mesh nodes. 

  - **board-autoconf.sh**
	(uses a static pathnames) ; 
        This script generates a random secret for the imageboard and asks the user for ADMIN_PASS and sets this in the configuraiton.

  - **delete_empty.sh**
        This script scans the folder given by the first parameter for 0Byte files and delets them. 

  - **distribute_files.sh**
        Used to distribute files into (sub-)directories.
        Can be switched to debug mode if exported env var. DEBUG=true
	Uses **distribute_file_into_directory.sh** to work on one folder.
        # destination folder
	# overwrite the exsisting files ("true|false") (optional)
	# File to distribute ( <pathname>|all) (optional)
            All is currently src/HEADER.txt & src/README.txt
	# PirateBox Script folder (optional)
        
  - **droopy**
        Python2 upload script, which is extended on some functions. Is **not** IPv6 capable. 

  - **exchange_www.sh**
        **obolete** script that moves www to the USB stick. N

  - **find_interface_name.sh**
       Module for new modulized startup. It is used for scripts that rely on (harcoded or generated) interface names. This script parses through the following configuration files and tries to find the first configured interface name: bridge.conf, network.conf, hostap.conf
       Script calls itself recursive.

  - **flush_dnsmasq.sh**
       Script to send SIGHUB to dnsmasq. **outdated, needs rework**

  - **install_piratebox.sh**
  
  - **json_generation.sh**

  - **piratebox_modules.sh**

  - **shoutbox_daemon.sh**

  - **station_cnt.sh**

  - **timesave.sh**

## hooks ##

  - **hook_pre_init.sh**
  - **hook_pre_openwrt_init.sh**
  - **hook_post_init.sh**



