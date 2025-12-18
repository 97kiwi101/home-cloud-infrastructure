# Network Security & Firewall Configuration

## Security Philosophy
This infrastructure operates on a **"Default Deny"** posture. All incoming traffic is blocked by default unless explicitly permitted. Access is managed through two layers:
1.  **Network Layer:** A Tailscale Mesh VPN (WireGuard) that authenticates devices before they can reach the local network.
2.  **Host Layer:** `firewalld` rules on individual nodes to restrict port access to specific services.

## 1. Gateway Node (Bastion Host)
**Role:** The entry point for the network. It exposes minimal ports to ensure the secure overlay network functions.

| Service | Port | Protocol | Source | Description |
| :--- | :--- | :--- | :--- | :--- |
| **SSH** | 22 | TCP | Local LAN / VPN | Secure Shell access for management. |
| **Tailscale** | 41641 | UDP | Any | Encrypted WireGuard tunnel traffic. |
| **DHCPv6** | 546 | UDP | Local LAN | Network IP assignment. |

### Configuration Commands
```bash
# Standard Bastion configuration
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --permanent --add-port=41641/udp
sudo firewall-cmd --reload