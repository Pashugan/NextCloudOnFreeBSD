# NextCloud on FreeBSD

Script to automate installation of Nextcloud on FreeBSD14+ and HardenedBSD14+
The finished installation passes all Nextcloud configuration checks.
This script follows recommended configuration as per https://docs.nextcloud.com/server/stable/admin_manual/installation/system_requirements.html

## Requirements

* Fresh install of FreeBSD 14+ / HardenedBSD 14+
* Lib32 for integrated DocumentServer support (this is the plugin version)
* ZFS. The pre-installer creates a new boot environment, which is not supported on UFS.

## Instructions

0. Read the instructions, and the scripts! :)
1. Clone repository or download release to your machine and extract.
2. `cd` to folder.
3. Switch to root by using `su`.
4. Run `pre_install.sh` as root to create a boot environment and config file before installing, then reboot before moving on.
5. `su` again after rebooting, and `cd` to the folder.
6. Open `install.conf` with your favourite editor.
   (Note: see https://www.php.net/manual/en/timezones.php for your time zone)
7. Change the values of variables as required to suite your environment.
8. Save the file.
9. Run `install.sh`
10. Please be patient while the script runs and drink your prefferred beverage.
11. Enjoy

**Installs the following:**

* Nextcloud 30
* Apache 2.4
* MariaDB 11.4
* PHP 8.3 (plus all required php-extensions)
* Redis
* ClamAV
* SSL Certificate (Let's Encrypt) using `certbot`
* Plugin version of the OnlyOffice document server, as a seperate step

------------

## Configuration

* Apache 2.4 + PHP using `php-fpm`
* HTTP/2 over TLS
* TLS1.3 only
* HSTS enabled
* APCu enabled
* Redis enabled (allows transactional file locking)

### NextCloud Apps Installed/Activated by default in config

* Antivirus for Files
* Calendar
* Contacts
* Deck
* Mail
* Notes
* Nextcloud Talk (Spreed)
* Tasks
* External storage support (including `samba` and `ftp`) (Can be disabled independently)
  
