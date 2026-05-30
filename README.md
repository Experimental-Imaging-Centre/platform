# EIC computational platform deployment

This repo contains the Ansible tools and scripts to deploy and maintain software across the EIC compute platform nodes. It is meant to supplement [Gabriel Devenyi's NeuroAnsible](https://github.com/gdevenyi/NeuroAnsible) by providing additional software (for data management, productivity, etc...) and analysis environments.

## Software

EIC-specific inventory definitions and skeleton files are hosted outside this repo. You will have to define your own hosts ("workstations").

## Running the code

Run a specific playbook:

```bash
# Run
ansible-playbook playbooks/provision_workstation.yml --ask-pass --ask-become-pass

# Override inventories specified in ansible.cfg, while also running a system upgrade via apt (safe)
ansible-playbook playbooks/provision_workstation.yml --ask-pass --ask-become-pass --inventory inventories/staging --tags all,system_upgrade

# Install the global environments
ansible-playbook playbooks/deploy_globalenv.yml --ask-pass --ask-become-pass

# Only install pip and CRAN packages, dry run
ansible-playbook playbooks/deploy_globalenv.yml --ask-pass --ask-become-pass --tags "pip,cran" --check
```
