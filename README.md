# Sustainable Home Cloud Infrastructure

## Project Overview
A distributed edge-computing cluster built entirely from rescued e-waste hardware. This project demonstrates Infrastructure as Code (IaC), Zero-Trust networking, and hybrid cloud architecture using Fedora Linux.

## Architecture
![Network Topology Diagram](diagrams/Cloud.png)


* **Gateway:** Fedora Server running on a Mini PC acting as a Bastion Host and VPN Subnet Router.
* **Compute Node:** High-performance Nobara Linux workstation for remote rendering (VDI).
* **Networking:** Tailscale (WireGuard) overlay network for secure remote access without port forwarding.

## Automation
I use **Ansible** to provision new nodes.
* `setup.yml`: Automates OS patching, package installation, and security configuration.
* `hosts.ini`: Defines the inventory of edge nodes.

## Key Technologies
* **Linux (Fedora/Nobara):** OS & Kernel management.
* **Ansible:** Configuration Management.
* **Tailscale:** Mesh VPN & Subnet Routing.
* **Moonlight/Sunshine:** Low-latency remote graphical streaming.
* **Bash Scripting:** Automated Wake-on-LAN power management.