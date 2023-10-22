# ansible-ubuntu-iptables
Ansible template to configure firewall on Ubuntu

## Installation

Create requirements.yml file

```
# Include ansible-ubuntu-iptables role
- src: https://github.com/FastMT/ansible-ubuntu-iptables.git
  name: ubuntu-iptables
  version: "v1.0.2"
```

Install external module into ~/.ansible/roles folder

```
ansible-galaxy install -r requirements.yml
```

## Usage

playbook.yml:

```
# Configure iptables
- role: "ubuntu-iptables"
    vars:    
      # Optional parameter to enable full access on interfaces
      iptables_allowed_interfaces:
        - "virbr0"
        - "wg+"
    
      # Optional parameter to configure outgoint nat to internet
      iptables_outgoing_nat_subnets:
        - "10.10.10.0/24"

      # Optional parameter to not save firewall rules to disk
      iptables_persistent: false

      # Optional parameter - custom ssh port (default: 22)
      linux_ssh_port: 122

```        