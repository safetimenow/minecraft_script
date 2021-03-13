![Pinecraft](assets/pinecraft-logo.png?raw=true)

## Minecraft Server Installer for Raspberry Pi, PINE64 and Other SBCs.

This installer simplifies the installation and setup of a Minecraft Server.

If you have already installed this, running it again will allow you to upgrade.

[![Support Me on Patreon](https://cdn.zecheriah.com/img/patreon_button.png)](https://patreon.com/pinecraft)

The installer will setup a "Normal" difficulty server and allow you to select between a Survival world complete with mobs, nether and more, or a Creative world to hone your skills as a master builder.

The installer attempts to detect things like how much RAM you have (and available), and adjusts the server settings based on what it finds.

Check out the first release, Pinecraft 1.0 on Category5 Technology TV:

[![Pinecraft Installer 1.0 Featured on Category5 Technology TV](https://img.youtube.com/vi/-8-7fQmhn2k/0.jpg)](https://www.youtube.com/watch?v=-8-7fQmhn2k)


Pinecraft Installer 1.0 was also featured on ameriBlog: https://ameridroid.com/blogs/ameriblogs/raspberry-pi-4-as-a-multiplayer-minecraft-server

The current version of Pinecraft is 2.1.

![Screenshot of Pinecraft Installer 2.0](assets/pinecraft-2.0.png?raw=true)


Server Versions
===============

**Paper** Supports Plugins / Fast Build Time

A performance-optimized Minecraft server based on Spigot and compatible with Spigot plugins. [More Info](https://papermc.io/)


**Fabric** Supports Plugins / Fast Build Time

A lightweight, modular Minecraft server. [More Info](https://fabricmc.net/)


**Spigot** Supports Plugins / Slow Build Time

An optimized server based on Craftbukkit, Spigot allows you to include mods in your server (both Spigot and CraftBukkit compatibility). Spigot will run a high-performance multiplayer Minecraft server on a Raspberry Pi 4 with 4GB or 8GB RAM, or other devices with a minimum of 4GB RAM. Spigot was the original Pinecraft default server, circa Pinecraft 1.x. [More Info](https://www.spigotmc.org/)


**Cuberite** (Currently Experimental) Slow Build Time

Cuberite is an alternate server which, while written in C++ accepts connections from Java clients. Note that you will need to use an old client to connect (currently supports 1.12.2). Advantage to Cuberite is that it will run on extremely under-powered devices, such as older Raspberry Pi.


**Vanilla** Fast Build Time

Vanilla is the official Mojang Minecraft server release. It does not allow mods, and is not as well optimized for SBC use, but will run great on a Raspberry Pi 4 with 4GB RAM or higher. [More Info](https://minecraft.net)


Game Modes
==========

**Survival**

Players must collect resources, build structures, battle mobs, eat, and explore the world in an effort to thrive and survive.


**Creative**

Creative mode strips away the survival aspects of Minecraft and allows players to easily create and destroy structures and mechanisms with the inclusion of an infinite use of blocks and flying.


We're open to suggestions. Let us know what you'd like to see.


Buy Your Raspberry Pi (Or Other SBC)
====================================

This feature on Category5 Technology TV sponsored by ameriDroid.com

[![ameriDroid](assets/ameridroid.png?raw=true)](https://ameridroid.com)

USA-based SBC sales with unmatched support and fast shipping

To power your Minecraft Server, get a Raspberry Pi 4 from https://ameridroid.com


Hardware Requirements
=====================

- A vanilla server OS based on Debian (such as Raspberry Pi OS Lite) with nothing else running and no desktop environment.
- If your board has more than 4 GB RAM, you must use a 64-Bit OS to utilize it effectively. Running a 32-bit OS will result in less RAM dedicated to your Minecraft Server.
- Minimum 4 GB RAM.
- GOOD Power Supply.
- Adequate Cooling for Overclock During Heavy Load.
- Reliable Storage Media (Kingston Endurance microSD or UASP-enabled USB 3 SSD).
- Ethernet connection to network (don't use Wi-Fi).


Software Requirements
=====================

- To play the game, you will need a valid Minecraft Java account, and to have Minecraft Java installed on your computer (Windows, Mac, AMD64 Linux). One account is required per player, and can be purchased from https://minecraft.net
- Debian-based headless server distro for your single board computer. For a Raspberry Pi 4, opt for Raspberry Pi OS Lite.

**Note:** You do not need a Minecraft Java account in order to run the server. I.E., you could boot up a Pinecraft server even without an account, and players with accounts can use it. However, it is quite handy to be able to sign in the game to moderate disputes or deal with grief. This can only be done if you have an account.


Plugin Support
==============

For any of the server versions which support plugins (see "Server Versions" above) simply place the plugin ZIP file in ~/minecraft/plugins and then run `~/minecraft/restart`

Remember, adding plugins can have a negative impact on your server performance. Some plugins may also introduce bugs, glitches or other issues. Be selective about which plugins you add to your server.

You can download plugins from https://www.spigotmc.org/resources/ or any other Bukkit / Spigot plugin resource.


License
=======

This project (Pinecraft, the install script) is free, open source software. However, Minecraft itself is not (hence why we are distributing an installer, not a pre-compiled distro). In order to use your Minecraft server, you must first accept the Minecraft EULA found here: https://account.mojang.com/documents/minecraft_eula

Of course, other projects utilized for Pinecraft carry other licenses (such as Java, Spigot, etc.). Ours is just an installer / configuration tool and we are not distributing any software.


Note About Backups
==================

Please consider automating a backup of your world. You can first stop the server with the provided `stop` script, then run your backup, and then restart your server with the provided `server` script.


Automated Overclocking
======================

If your board is supported and tested by me, the installer will automatically set overclock settings to maximize performance.

Therefore, you must absolutely ensure your power supply is a good one. We'll be using a bit more power than normal.

You are welcome to adjust the overclock settings if desired. However, I would recommend trying my defaults first.

I have chosen to be conservative with my overclocking for two reasons:

1) I want you to get the best possible performance out of your Minecraft server, but also wish to ensure it is rock-solid stable.
2) I do not want to void your warranty. I.E., I will NOT enable force_turbo.
3) I do not wish to damage your Pi.

When I overwrite your /boot/config.txt file, I first create a backup of your original at /boot/config-DATETIME.txt, so if you're unable to boot for some reason, hopefully you can easily recover. Note that you are running this script at your own risk, and I am not responsible for anything that happens as a result of your running this installer. Except smiles. I'll accept responsibility for smiles.


Usage
=====

Run the installer immediately following a fresh reboot (to avoid having residual apps taking up RAM thereby resulting in less RAM allocated to your game server).

The command is simple:

`sudo ./install`

Once installation is complete, you must reboot for the server to begin functioning. If you selected to auto-load at boot, your server will immediately begin generating the world on first boot. Otherwise, you'll need to run the server manually.

To reboot **do not** use traditional Linux commands. You must use:

`sudo ~/minecraft/reboot`

### Important Note: First Boot

On first boot, your Minecraft Server will generate the world. This can take around 10 minutes, so hang tight while this happens, and then connect to your Minecraft Server's IP address from Minecraft Java as soon as it is ready. You can tail the log file if you'd like to see the progress, or sipmly retry connecting via Minecraft Java after a few minutes.


Post-Install Scripts
====================

### ~/minecraft/server
Start the Minecraft server. This script is automatically run upon boot.

### ~/minecraft/reboot
When you need to reboot your Minecraft server, you must do so safely, otherwise all blocks that are stored in RAM will be lost (could be a full day's worth). Run this script to shutdown the Minecraft server software, store all blocks, and reboot the server. Note: It can easily take 15-20 minutes to stop the Minecraft server. Don't abort once you run this script. It is working hard to save all the blocks for your world and if you stop it or force a reboot, you will lose blocks.

### ~/minecraft/stop
Safely stop your Minecraft server. DO NOT reboot your system or power off unless you have first run this script and allowed it to complete.


Networking
==========

Your Minecraft server runs on port 25565. If you'd like others to be able to join your server, forward that port to your Minecraft server in your firewall.

Within your LAN, you can access your Minecraft server by the IP address of your Raspberry Pi Minecraft server.

**Note:** If you open up your server to the world you introduce the risk of someone connecting and griefing (damaging your builds). To protect your server world, either limit the logins to specific users (see Minecraft documentation), restrict your firewall to only allow trusted IPs that you specify (see your networking documentation) or if you truly want it to be a public server, add some mods to protect your world (see Spigot documentation).

Log Files
=========

### ~/minecraft/logs/latest.log
The current Minecraft Server log file. You can run `tail -f ~/minecraft/logs/latest.log` on your Minecraft Server to see what's happening. Logs are rotated and gzipped by date.


Version History
===============

Pinecraft 2.1 - Added Vanilla server. Label Paper as the new Default server version (previously was Spigot). Hide output of installers (to hide the misleading errors in Paper's installer). Added experimental support for Cuberite.

Pinecraft 2.0 - Pinecraft now supports installation of Paper, Fabric, and Spigot. Also, previous versions deployed a Survival server. Now, user may choose Survival or Creative during install.

Pinecraft 1.1 - New installer interface.

Pinecraft 1.0 - Initial release, installs, configures and optimizes a Spigot Minecraft server, as seen on Category5 Technology TV.


Troubleshooting
===============

### Server gets killed by Linux
Try `dmesg -T| grep -E -i -B100 'killed process'` after this happens to see why Linux killed the process. It is most likely you are running other applications on your system (which is a big no-no) and have run out of resources. You should only run this on a completely headless SBC, with no desktop environment, and nothing else running. You can adjust the amount of RAM allocated by editing the `server` script in ~/minecraft

### Overclock says N/A
The type of hardware you're using hasn't been tested by me, and I haven't added automatic overclocking for your board. You'll need to perform your own overclocking. If you do so successfully, please let me know what you had to do, and if I can test it, I may add it to a future update.

Post-Install Configuration
==========================

Give your Minecraft server a try before you start changing the config. It's very possible to break things if you modify the config, so it's a good start to test your server first, and then just tweak what's needed / desired.

You'll find your config file here: ~/minecraft/server.properties

Mojang Documentation: https://minecraft.gamepedia.com/Server.properties#Java_Edition_3


Frequently Asked Questions
==========================

Remember, Pinecraft Installer installs a Minecraft server like any other. Our goal is to make it easy for you to get up and running with an efficient, high-performance server, but we don't rework how the resulting server works in any way. Therefore, the official Minecraft docs are the perfect place to get help with your server configuration.

That said, we get some questions regularly, and we're here to help if we can, so we'll record them here.


**First, here are some helpful links:**

Modify server.properties, the main config file for your server's settings
https://minecraft.gamepedia.com/Server.properties#Java_Edition_3

**Find Plugins for Spigot / Paper / Fabric**
https://www.spigotmc.org/resources/categories/spigot.4/

**Don't Forget:** Plugins can negatively impact server performance. Select carefully.


**And here are some FAQ's:**

*How do I become admin? /op says I don't have permission.*

After connecting to your server as the user you want to make admin, look at your `~/minecraft/logs/latest.log` file and find the UUID for that user.

Edit `~/minecraft/ops.json` as follows:

```
[
  {
    "uuid": "UUID",
    "name": "USERNAME",
    "level": 4
  }
]
```

Replace UUID with your UUID, and USERNAME with the actual username. Then, restart your Pinecraft server with `~/minecraft/reboot`

When your server comes back online, that user will be admin, and can now use the /op command to create other admins.
