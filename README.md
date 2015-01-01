# DevCon Ansible Playbook

This is an [Ansible](http://ansible.com/) playbook to recreate the [DevCon](http://devcon.ph/) server.

## What this installs

* DevCon web page
* Old static pages (e.g. Summit)
* Analytics software (Piwik)

## Setup

This script requires a backup file named `backup.tar.bz2` on the current folder, ensuring that only the ED, President, or VP Technoology can run this script.

Apart from the backup file, you also need to modify the variables under `group_vars/all` before running this script.

Once the two are ready, do the following steps to provision a new DevCon server:

1. Provision an Ubuntu 14.04 server, preferrably a Digital Ocean server in the Singapore data center. Add your SSH key for root access.
2. Copy `hosts.example` to `hosts` and replace the `localhost` inside with the IP address of the new server.
3. Run `ansible-playbook -i hosts devcon.yml`. The script will restart the server at the end.
4. After the server restart is finished, run `ansible-playbook -i hosts devcon-finish.yml` to complete the provisioning.
5. Deploy the DevCon website using Capistrano. [See site source for details.](https://github.com/devcon-ph/devcon)
6. Check if all subdomains are working correctly (default, analytics, summit, etc).
7. Manually setup the non-open-source backup script.
7. If you're using Digital Ocean or any VPS that doesn't allocate swap space, allocate the appropriate amount of swap space using [this guide](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04).

