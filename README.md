# Baremetal Lab

Turn a dual-NIC mini PC into a full home lab: OPNsense, Docker, Home Assistant, ESPHome, Frigate, and more.

## Web generator

Configure hardware and services in the browser, then download a `docker-compose.yml`:

**https://wilcox101-maker.github.io/baremetal-lab/**

## USB boot path

No OS installed yet? See [USB-BOOT.md](USB-BOOT.md) for Ventoy / Debian / Proxmox options.

## Local script

```bash
git clone https://github.com/wilcox101-maker/baremetal-lab.git
cd baremetal-lab
chmod +x setup.sh
./setup.sh
```

## Recommended architecture

```
Internet → OPNsense (VM) → LAN
                ↓
         Docker host (LXC/VM)
           ├── AdGuard Home
           ├── Unbound
           ├── Home Assistant
           ├── ESPHome / Mosquitto
           ├── Nextcloud / Immich
           ├── Grafana / Prometheus / Uptime Kuma
           ├── Nginx Proxy Manager
           └── Tailscale
```

## Hardware notes

| Component | Recommendation |
|-----------|----------------|
| CPU | i3 10th gen or better |
| RAM | 8 GB minimum, 16 GB comfortable |
| NICs | Dual Intel Ethernet preferred |
| Wi-Fi | Separate AP (or USB adapter) |
| Storage | NVMe/SSD for Nextcloud / HA / Immich / Frigate |

## Files

| File | Purpose |
|------|---------|
| [index.html](index.html) | Web generator |
| [setup.sh](setup.sh) | Local interactive configurator |
| [USB-BOOT.md](USB-BOOT.md) | USB installer path |
| [STACK-GUIDE.md](STACK-GUIDE.md) | Full service reference |

## License

MIT
