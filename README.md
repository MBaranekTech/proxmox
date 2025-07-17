# 🖥️ Proxmox virtualization

a powerful open-source platform for enterprise virtualization. <br>
It integrates KVM (Kernel-based Virtual Machine), LXC containers, software-defined storage, and network management into a unified web interface. <br>

Using for managing virtual machines, containers, storage, and networks. Built on top of KVM and LXC, I help you run everything from small home labs to full-scale enterprise systems. With features like high availability, backups, clustering, and an intuitive web GUI, I make IT infrastructure powerful, flexible, and efficient – no license fees required.

How to start with Proxmox

1. Download Proxmox VE
Go to [Proxmox Downloads](https://www.proxmox.com/en/downloads) and grab the latest Proxmox VE ISO Installer.
2. Create a Bootable USB
Use tools like balenaEtcher, Rufus (Windows), or dd (Linux/macOS) to flash the ISO onto a USB stick.

3. Install Proxmox
Boot your target machine from the USB.

4. Test Access
   After the reboot, you'll get access to the web UI via:
https://your-ip-address:8006

4. Login to Web Interface
Use the credentials you set during installation.

How upload ISOs & Create VMs:  <br>
Go to Datacenter → Node → local → ISO Images to upload your OS ISOs.

# Key features:

Via Proxmox dashboard you can: <br>
Create virtual machines (KVM) <br>
Launch LXC containers <br>
Set up storage ZFS LVM <br>
Configure networking and firewalls <br>
Enable backups and HA <br>


# 🚀 First mini project with Proxmox: Install Pi-hole in LXC on Proxmox
Pi-hole is ad blocking in your network.

Run these commands in the Proxmox shell and download a Debian Container Template:
```
pveam update
pveam available | grep debian
```
<img width="593" height="526" alt="5" src="https://github.com/user-attachments/assets/82fbaae1-8e52-4b5c-bca4-9cff00bd3225" /><br>
```
pveam download local debian-12-standard_12.7-1_amd64.tar.zst
```
Create LXC Container for Pi-hole
Via Datacenter - Node - Create CT 
```
Hostname: pihole
Template: debian-12-standard
Disk Size: between 4–8 GB
CPU/RAM: 1 vCPU, 512–1024 MB RAM
Network: Static IP or DHCP
```
<img width="725" height="537" alt="1" src="https://github.com/user-attachments/assets/4f8a4558-6fc4-443f-bba6-37215183f49f" />


Start LXC container and install Pi-hole <br>

You can access container via GUI or via Root Proxmox shell
<img width="1264" height="522" alt="4" src="https://github.com/user-attachments/assets/e7e196d4-71bd-4d89-a08b-73c8f29fba06" />

```
From terminal pct enter <CTID>
```
Update packages:
```
apt update && apt upgrade -y
```
Install Pi-hole:
```
curl -sSL https://install.pi-hole.net | bash
```
Follow the installation steps and access web admin url ```http://<your-container-ip>/admin```

<img width="507" height="681" alt="6" src="https://github.com/user-attachments/assets/168be731-2ef2-4af4-98f9-7c3495fe993e" />

Change password for service. You can do it only via command.
```
pihole -a -p
```


