# Module 02 — Linux, Networking & Cloud Infrastructure

## Codomax Digital Solutions | Cloud Computing & DevOps Internship

### Objective
Implement and validate a Linux server, secure remote access, network connectivity, users/groups/permissions, host firewall, and a web service.

### Lab environment
| Component | Implemented configuration |
| --- | --- |
| Hypervisor | VMware Workstation (local lab) |
| OS | Ubuntu Server 26.04.1 LTS |
| Hostname | `codomax-ubuntu-m02` |
| Network | VMware NAT; `ens33` |
| Lab IP at validation | `192.168.118.129/24` (DHCP; may change) |
| Default gateway | `192.168.118.2` |
| Remote administration | OpenSSH with Ed25519 public-key authentication |
| SSH hardening | Password and keyboard-interactive authentication disabled; root SSH login disabled |
| Firewall | UFW: deny incoming by default; TCP 22 allowed only from `192.168.118.1`; TCP 80 allowed for HTTP |
| Web server | NGINX 1.28.3 |
| Access validation | Successful SSH public-key login, HTTP 200 from localhost, and access from Windows browser |
| Users & groups | `codomaxlab`, `codomax-m02` |
| File permissions | `/srv/codomax-m02` mode 2770, test file mode 640 |

### Implementation
1. Provisioned a Linux VM with 2 GB RAM, two CPU cores, 20 GB disk, and NAT networking.
2. Installed Ubuntu Server and OpenSSH.
3. Verified SSH access, then configured Ed25519 key authentication and SSH hardening.
4. Created an additional lab user and group, applied ownership and Linux permissions.
5. Verified Linux services, processes, IP configuration, routes, DNS, and listening ports.
6. Enabled UFW with restricted SSH access and permitted HTTP.
7. Installed NGINX and deployed a custom module landing page.
8. Validated `nginx` active/enabled, `curl -I http://localhost` returning HTTP 200, and access through the host browser.

### Evidence and documentation
The final report, architecture diagram, and sanitized screenshots of actual tests belong under `docs/` and `evidence/`. Only publish screenshots after checking for credentials, SSH private keys, personally identifying details, and irrelevant host information.

### Scope and limitations
**This is a local VMware deployment, not an Azure VM or production cloud deployment.** Azure network security groups and other managed cloud resources were not provisioned. The module uses Azure as a conceptual architecture reference, while practical steps were performed on a local VM. The private NAT address is not a publicly accessible cloud endpoint.

### Security notes
Never commit VM disks, ISO files, SSH private keys, passphrases, tokens, or other secrets. The repository's root `.gitignore` excludes common sensitive artifacts.
