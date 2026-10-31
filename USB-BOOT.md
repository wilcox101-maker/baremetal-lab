# USB Boot Environment

Get a dual-NIC mini PC ready to run the lab without a pre-installed OS.

## Option A — Ventoy + Debian live (recommended)

1. Download [Ventoy](https://www.ventoy.net/) and install it on a USB stick (8 GB+).
2. Copy these ISOs onto the Ventoy USB:
   - **Debian 12 netinst** or **live** ISO
   - **Proxmox VE** ISO (optional, for the hypervisor path)
3. Boot the machine from the USB.
4. Install Debian 12 (or Proxmox) to the internal drive.
5. After first boot:
   ```bash
   git clone https://github.com/wilcox101-maker/baremetal-lab.git
   cd baremetal-lab
   ./setup.sh
   ```

## Option B — Proxmox direct

1. Download the Proxmox VE ISO.
2. Write it to USB with Rufus, balenaEtcher, or `dd`.
3. Boot and install Proxmox to the internal drive.
4. In the Proxmox shell, create an LXC or VM for Docker and follow the stack guide.

## After the base OS is installed

1. Open the generator: https://wilcox101-maker.github.io/baremetal-lab/
2. Select hardware and services, download `docker-compose.yml`.
3. On the Docker host:
   ```bash
   mkdir -p /opt/stack
   # copy docker-compose.yml into /opt/stack
   cd /opt/stack
   docker compose up -d
   ```

## Hardware checklist

| Item | Notes |
|------|-------|
| Dual Ethernet | Prefer Intel NICs; note which port is WAN vs LAN |
| RAM | 8 GB minimum, 16 GB comfortable |
| Storage | NVMe/SSD recommended |
| USB stick | 8 GB+ for the installer |
