## Changelog

version 0.8.4 (samicrusader's fork):
- [new] packaged for Debian/Ubuntu
- [bugfix] more "detailed" logging for iptables failures

version 0.8.3 (samicrusader's fork):
- [new] dbus used for changing config instead of requiring qomui-gui to be ran as root
- [change] reformat code
- [change] use Quad9 for alternate DNS
- [change] clean up apply log
- [bugfix] handle nftables (temporarily)
- [bugfix] plotter fix
- [bugfix] pull default interface name from gateway

version 0.8.2:
- [new] added AzireVPN
- [new] option to specify key for Airvpn
- [change] fast/random option added to profiles
- [change] order of latency checks now based on previous results
- [change] tidied up directory structure
- [change] checks if ipv6 is available
- [change] auto-updates for different providers won't run concurrently
- [change] check if IPv6 is available before setting iptables rules
- [change] don't generate new WireGuard keys on auto-update
- [change] allow importing new servers if firewall is active but VPN is not
- [bugfix] firewall not deactivating after gui exit (if the respective option is set)
- [bugfix] detection of service crashes is not reliable
- [bugfix] Windscribe auto-update fails because of authentication error
- [bugfix] compatibility with older Qt5 versions 
- [bugfix] previous iptables rules not always restored
- [bugfix] crashes if ipv6 stack not available
- [bugfix] OpenVPN config changes overwritten on update
- [bugfix] Debian packages remove /usr/share/qomui directory on update

##### Additional notes:
- Re-importing config files from supported providers is strongly recommended as they are now saved in a different location. 
- If you are using Debian/Ubuntu packages Qomui must be removed (sudo apt purge qomui) and then installed again due to a bug in the postrm script. 

version 0.8.1:
- [change] option to restart qomui-service from gui if it crashes
- [change] added exceptions for all DBus calls
- [change] improved support for non-systemd distributions
- [change] detecting and closing simultaneously running instances
- [bugfix] Airvpn auto-download fixed

version 0.8.0:
- [new] connection profiles 
- [new] support for custom scripts
- [change] configurations for Airvpn are now downloaded directly
- [change] removed minimize option if system tray not available
- [change] download new Mullvad config/certificates  
- [change] added scroll areas to some tabs
- [change] added options for profiles to tray menu
- [change] window state now recognized correctly
- [bugfix] improved stability and reliability of network detection 
- [bugfix] manually imported WireGuard servers don't connect
- [bugfix] Qomui crashes when downloading Airvpn configs
- [bugfix] fixed Mullvad & Windscribe configs

version 0.7.4:
- [change] source and binary packages now provided by [OpenSuse Build Service](https://build.opensuse.org/)
- [change] added support for OpenSuse Leap 15 and OpenSuse Tumbleweed
- [change] split Qomui into more modules and started commenting code
- [bugfix] bypass tab not shown even though it is active
- [bugfix] progress bar shown twice for the same action
- [bugfix] manually adding config files fails if "proto" line not present
- [bugfix] import may fail if directory for certificates/keys does not exist
- [bugifx] timestamp not updated after auto-updating servers 

version 0.7.3:
- [change] firewall is reloaded on gui startup 
- [change] checking for presence of other firewall services such as ufw when configuring firewall
- [change] selection box for protocols adjusts size 
- [bugfix] previous iptables rules are now properly saved/restored
- [bugfix] sometimes external ip is displayed twice
- [bugfix] Qomui crashes when adding folder and provider not specified
- [bugfix] WireGuard dns-servers not set correctly when second tunnel in bypass active
- [bugfix] manually imported WireGuard configs are not added to server list - [issue #24](https://github.com/corrad1nho/qomui/issues/24)
- [bugfix] potential permission error for temporary files created during importing configs

version 0.7.2:
- [change] cli supports new import and connection methods
- [bugfix] timer for connection attempts may close active OpenVPN tunnel
- [bugfix] multiple widgets shown if bypass VPN reconnects
- [bugfix] wait cursor doesn't always reset
- [bugfix] Openvpn not reconnecting when process dies unexpectedly

version 0.7.1:
- [new] secondary vpn tunnel in bypass mode - EXPERIMENTAL
- [change] download statistics switch to higher units automatically
- [change] using QThread for OpenVPN/WireGuard process now
- [change] using alternative url if checking external ip address fails
- [change] 20 sec timeout for Openvpn connections attempt
- [bugfix] some temporary files not deleted after importing servers
- [bugfix] Qomui doesn't recognize when OpenVPN connection attempts fail due to fatal errors

version 0.7.0:
- [new] auto-update for supported providers - EXPERIMENTAL
- [change] server import method rewritten
- [change] using libnotify for notifications - QMessageBox as fallback
- [change] Windscribe naming scheme changed - Windflix servers now recognizable
- [change] ProtonVPN naming scheme changed to make Free, P2P, Tor & SecureCore servers more visible
- [change] search bar for filtering servers
- [change] network connectivity monitoring: relying on sysfs instead of network-manager
- [change] Qomui does not rely on systemd anymore - although it is still recommended
- [change] Mullvad certificates are now downloaded from github 
- [¢hange] PIA: compression disabled in config file - [issue #22](https://github.com/corrad1nho/qomui/issues/22) 
- [bugfix] installing deb-package fails on Debian Stable - dependencies updated
- [bugfix] restore of original DNS servers more reliable 
- [bugfix] ordering of servers after latency check more reliable
- [bugfix] loop when version discrepancy between qomui-gui and qomui-service detected and qomui-service has not been started via systemctl
- [bugifx] crash if failing to read/start desktop-file - will be further investigated
- [removed] simple tray option 

version 0.6.5:
- [change] automatic restart if background service is running an older version than the gui
- [change] pending tasks such as connecting to a server can be cancelled now
- [change] multiple progress bars are now shown for concurrent actions
- [change] string formatting changed to new style
- [change] dropped pycountry dependency - using simple json instead
- [change] added more log messages
- [change] added log levels
- [change] external ipv6 address displayed (if available)
- [bugfix] crashes when trying to modify server when none is selected

version 0.6.4:
- [change] added new firewall options
- [change] code cleanup
- [change] WireGuard connections now honor DNS override
- [bugfix] Proton api url updated
- [bugfix] added all local ipv4 ranges 

version 0.6.3:
- [change] bypass mode supports ipv6 now
- [change] alternative DNS servers are used for bypass
- [change] WireGuard is now written correctly (pull request from zx2c4) - requires all WireGuard configs to be readded
- [change] exit dialog has a 5 sec timeout now
- [change] umask set before chmod to avoid race conditions (pull request from zx2c4)
- [bugfix] bypass should now work properly with WireGuard connections

version 0.6.2:
- [change] api-url for ProtonVPN updated - the one introduced in last update was out of date
- [change] added support for Windscribe's stealth feature (OpenVPN over SSL)
- [change] postrm functions added to deb/rpm/aur packages 
- [change] automatic reconnections for double hop if first hop fails/disconnects
- [change] adjusted OpenVPN configs of Mullvad and Windscribe to match official ones
- [bugfix] tray icon not always updated after establishing double hop connection 
- [bugfix] qomui crashes while performing latency checks when server(s) are deleted

version 0.6.1:
- [new] support for Windscribe
- [new] support for ProtonVPN
- [change] missing flags for Windscribe added
- [change] autocompletion for "c" and "v" options in cli
- [change] most cli commands are not case-sensitive anymore
- [bugfix] alternative dns servers not parsed correctly
- [bugfix] crashes when loading default configuration
- [bugfix] configs are not imported if url cannot be resolved
- [bugfix] old connection not killed after network change detected (in rare cases)

version 0.6.0:
- [new] support for WireGuard
- [new] cli-interface
- [change] additional parameters parsed from .desktop-files
- [change] update routine now uses dpkg/rpm if installed as DEB/RPM package - reinstall required!
- [bugfix] crashes at start when system tray not available
- [bugfix] Info for active connection sometimes not updated correctly 
- [bugfix] Doublehop fails on Fedora

version 0.5.1:
- [new] support for ipv6/tls-crypt configs from AirVPN - EXPERIMENTAL
- [bugfix] firewall dialog not opening on new installations
- [bugfix] random crashes when tunnel interface not available
- [bugfix] update offered even though latest version installed

version 0.5.0:
- [new] Reconnect when OpenVPN unexpectedly dies
- [new] Update Qomui via new "About" tab - EXPERIMENTAL
- [new] Option to use simplified tray icon to avoid glitches
- [new] Protocol/port of active connection displayed
- [new] Tray icon shows connection status 
- [new] Automatic reconnects when OpenVPN tunnel breaks
- [change] Disconnect button always visible
- [bugfix] Config file / firewall configuration overwritten after update
- [bugfix] Crashes due to missing entry in config file
- [bugfix] Crashes when modifying server during latency check
- [bugfix] Changing country in modify dialog fails
- [bugfix] Connection attempt fails when protocol/port not set
- [bugfix] WireGuard servers downloaded from Mullvad even though not supported

version 0.4.1:
- [bugfix] Crashes if no port/protocol selected
- [bugfix] Crashes while performing latency checks if not connected to a network
- [bugfix] Tray icon not displayed on Linux Mint Cinnamon 18.3
- [bugfix] Cannot toggle "autoconnect" option
- [bugfix] Crashes if checking latencies while new servers are added

version 0.4:
- [new] Check and sort servers by latency
- [new] Additional info for active connection displayed 
- [bugfix] Disable ipv6 option status not displayed correctly
- [bugfix] List of applications is empty if not all default application directories exist
- [bugfix] Minimizing/maximizing window does not work on Mint Cinnamon 18.3

version 0.3.1
- [new] Modify imported servers and config files
- [change] Improved performance of server list
- [change] Mullvad: Updated link to parse server info
- [bugfix] Crashes when deleting server/provider fixed
- [bugfix] Memory leak in server tab fixed

version 0.3
- [new] Mark servers as favourites
- [new] Randomly connect to a favourite server
- [new] Support for PIA (PrivateInternetAccess)
- [new] Override Port/Protocol in imported configs
- [change] Config file import improved
- [change] All servers displayed in one tab
- [bugfix] Crashes after hibernate

version 0.2
- [new] OpenVPN bypass
- [change] DNS management
