# jd2-openvpn-plexguide
Compose file for Plexguide of h1f0x/jd2-openvpn

Documentation of the image and how it works can be found at: 
- https://github.com/h1f0x/jd2-openvpn

# How to install?

IMPORTANT: You are not able to run jDownloader2 and jDownloader2+OpenVPN at the same time. Same port usage needed. Please remove non-VPN app first.

## Manual Install
1. Copy the jd2-openvpn-plexguide.yml to "/opt/mycontainer/"
2. Run plexguide and install the application via the community option

## Via PG Community
tbd -> not yet added

# Post-Installation Tasks
1. Prepare config.ovpn:
   1. add the following lines to your custom OpenVPN config

     ```
    script-security 2
    up /etc/openvpn/up.sh
    down /etc/openvpn/down.sh
    
    Example of an ExpressVPN configuration in ./example/example.config.ovpn
    ```

2. Copy & past your vpn config to /opt/appdata/jd2-openvpn/vpn/config.ovpn
   1. IMPORTANT: the vpn configuration needs to be named: config.ovpn
   2. if you have user-pass-auth:
        1. add the line "auth-user-pass vpn.auth" to your config.ovpn
        2. create a text file at the same location named "vpn.auth"
        3. add the username on the first line
        4. add the password on the second line

3. Wait about 2 minutes for the cron to kick in and reconnect you to your vpn!
4. You can access your new jDownloader like the non vpn one and configure it to you r needs.

# Trivia
You can verify your current external ip address by checking the logfile at:
```
cat /opt/appdata/jd2-openvpn/vpn/current_external_ip.txt
```
    