📂 [**Click Here**](https://goo.gl/7NR3Da) - Sign up for Google's Suite for Business - Unlimited Space

📂 [**Click Here**](https://controlpanel.newshosting.com/signup/index.php?promo=partners&a_aid=5a65169240efd&a_bid=5ecfe99b) - NZB's with from NewsHost - PG Members Receive a 58% Discount

<p align="center">
  <a href="https://plexguide.com/forums" target="_blank"><img src="https://plexguide.com/wikipics/logo-forums.png" width="160"/>   
  <a href="https://github.com/Admin9705/PlexGuide.com-The-Awesome-Plex-Server/wiki" target="_blank"><img src="https://plexguide.com/wikipics/logo-wiki.png" width="160"/>
  <a href="https://plexguide.com/threads/plexguide-install-instructions.243/" target="_blank"><img src="https://plexguide.com/wikipics/logo-pg-install.png" width="160"/> 
  <a href="https://plexguide.com/account/upgrades" target="_blank"><img src="https://plexguide.com/wikipics/logo-donate.png" width="160"/>
</p>

__________________________________________________________________________________________________________

# 1. Introduction

This a merged docker image created of two separate images:

- dperson/openvpn-client (https://github.com/dperson/openvpn-client)
- jlesage/docker-jdownloader-2 (https://github.com/jlesage/docker-jdownloader-2)

Instructions for each images can be found at the specific GitHub page.

The GitHub for this base image can be found at:

- h1f0x/jd2-openvpn (https://github.com/h1f0x/jd2-openvpn)
- h1f0x/jd2-openvpn-plexguide (https://github.com/h1f0x/jd2-openvpn-plexguide)

----------------------------------------------------------------------------


# 2. Specified Features

## Overwall
* Tunnels the JDownloader2 traffic into a VPN tunnel of your choice!
* Supports all the features of the already existing JDownloader2 Image for Plexguide
* Even with OpenVPN on, its working with Traefik

## JDownloader2

* Versions run under (Microsoft Windows, Linux, Mac, etc.), and Java 1.5 or higher
* Can download several files simultaneously, over several connections
* Can automatically solve some CAPTCHAs with its own OCR module (JAntiCaptcha)
* Automatic extractor (including password list search) for RAR archives
* Decrypt RSDF, CCF and DLC Container files
* About 300 decrypt plugins for many services. For example, sj.org, UCMS, WordPress, and RLSLog.
* Supports "hoster plugins" for downloading from e.g. a specific one-click hoster (1230 as of 2014)[9]
* Can automatically acquire a new IP address to save waiting time with hosts which limit downloads to one address (1400 routers supported)
* Integrated package manager for additional modules (e.g., Web interface, Shutdown)
* Theme support
* Multilingual

## OpenVPN Client
* Theoretically Supporting all features the original image does
* automated connection after docker start
* Currently only using config.ovpn:
    1. certificate authentication
    2. user-pass authentication

-----------------------------------------------------------------------------------------------------------

# 3. How to install

## Pre-Install Tasks

### Prepare OpenVPN configuration

* Add the following lines to your custom OpenVPN config:

    ```
    # Mandatory
    script-security 2
    up /etc/openvpn/up.sh
    down /etc/openvpn/down.sh
    
    # If User/Password Auth -> add username, password to vpn.auth file
    auth-user-pass vpn.ath

Example of an ExpressVPN configuration in https://github.com/h1f0x/jd2-openvpn-plexguide/blob/master/exmaple/example.config.ovpn

## Installation

That's the way to install Jdownloader2 with integrated OpenVPN on your PGServer with Traefik and Google OAuth

1 . ``` plexguide ``

2 . ``` [5] Box Apps: Community ```

3 . ``` [1] Utilize Community Box - PlexGuide's ```

4 . ``` jd2-openvpn```

5 . ``` deploy ```

6 . ``` docker stop j2-openvpn```

7 . ``` cp /path/from/config.ovpn /opt/appdata/jd2-openvpn/vpn/config.ovpn [Note: Copy all files you need for authentication!]```

8 . ``` docker start j2-openvpn```


Wait about two minutes.

## Post-Installation
Verify your current ip address by:

````cat /opt/appdata/jd2-openvpn/vpn/current_external_ip.txt````
