# Ansible Docker Wireguard
This repo sets up wireguard docker container using ansible. I'm using ansible to build out the directory structure, and then create the `docker-compose.yml` file. Then ansible uses docker-compose to verify that the container is running. 


## Support
Currently this ansible setup only supports Debian.

## Requirements 
There are no major requirements at this time. Obviously you need ssh access to the host that will be running your docker container(s). This repo will install docker if you don't already have it installed. *nice*

## Variables
All of the variables are in vars/main.yml. You'll want to change the `wg_serverurl` variable to your public ip address, *(if you have a public DHCP address then use whatever dynamic dns name you are using)*.

## Setup
  1. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html). The easiest way (especially on a Debian system) is via Pip:
     1. `sudo apt-get install -y python3-pip`
     2. `pip3 install ansible`
  2. Clone this repository: `git clone https://github.com/frame45/ansible-docker-wireguard.git`, then enter the repository directory `cd ansible-docker-wireguard`. 
  3. Make copies of the following files and customize them to your liking:
     - `example.inventory.ini` to `inventory.ini` (replace IP address with your docker host's IP, or comment that line and uncomment the `connection=local` line if you're running it on the docker host you're setting up).
     
  4. Run the playbook: `ansible-playbook main.yml`

## Usage
  1. You will need to copy the config located in the `docker_project_src/config` directory, to your client pc.

> **Example:** the first peer config is located in: `docker_project_src/config/peer1/peer1.conf` this is the file that you add to your wireguard client pc. 

  2. You need to add the [port-forward](https://portforward.com/) rule to your network router/firewall device. 

  3. That's it!

## Credit
I directly stole the `docker.yml` file for installing docker from [Jeff Geerling](https://www.jeffgeerling.com/)'s [internet-pi](https://github.com/geerlingguy/internet-pi) repo. It works great for me so I'm not re-inventing the wheel for this. 

## License

MIT

## Author

Created by Matt Yakel in 2023.
