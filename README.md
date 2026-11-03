# netauto — Network Automation Starter

Python (Netmiko) + Ansible toolkit for config backups, inventory facts, and basic compliance checks on Cisco devices.

## Layout
```
inventory/hosts.yml        Ansible inventory
inventory/devices.yaml     Inventory for the Python scripts
playbooks/backup_configs.yml
playbooks/show_version.yml
scripts/backup_configs.py  Netmiko config backup
scripts/compliance_check.py  Checks configs for required/forbidden lines
backups/                   Saved running-configs (git-ignored)
```

## Setup
```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
ansible-galaxy collection install cisco.ios ansible.netcommon
export NET_USER=admin NET_PASS='your-password'
```
Credentials come from environment variables — never commit them.

## Usage
```bash
# Python
python scripts/backup_configs.py
python scripts/compliance_check.py

# Ansible
ansible-playbook playbooks/show_version.yml
ansible-playbook playbooks/backup_configs.yml
```
Edit the inventory files with your real device IPs first (the ones included are placeholders).
