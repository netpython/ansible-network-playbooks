# Ansible Network Playbooks

**160 read-only playbooks for network operations across eight platforms.**

Collect inventory, inspect protocol state, review firewall policy and capture evidence for a change window. Each playbook targets a named inventory group and saves a separate JSON report per device on the controller.

`Ansible Core` · `Network CLI / NETCONF / API` · `160 platform playbooks`

## Pick a platform

| Platform | Playbooks | Inventory group | Connection |
| --- | ---: | --- | --- |
| [Cisco IOS](cisco-ios/README.md) | 20 | `ios` | `ansible.netcommon.network_cli` |
| [Cisco IOS XE](cisco-ios-xe/README.md) | 20 | `ios_xe` | `ansible.netcommon.network_cli` |
| [Cisco NX-OS](cisco-nx-os/README.md) | 20 | `nx_os` | `ansible.netcommon.network_cli` |
| [Juniper Junos](juniper-junos/README.md) | 20 | `junos` | `ansible.netcommon.netconf` |
| [Aruba AOS-CX](aruba-aos-cx/README.md) | 20 | `aruba` | `ansible.netcommon.network_cli` |
| [Palo Alto PAN-OS](palo-alto-pan-os/README.md) | 20 | `panos` | `local` |
| [FortiGate / FortiOS](fortigate-fortios/README.md) | 20 | `fortios` | `ansible.netcommon.httpapi` |
| [Check Point Management API](check-point-gaia/README.md) | 20 | `checkpoint` | `ansible.netcommon.httpapi` |

## Setup

Use Python 3.11 or later on a Linux controller. Install the Python dependencies and vendor collections before running a play.

```bash
git clone https://github.com/netpython/ansible-network-playbooks.git
cd ansible-network-playbooks
python3 -m venv .venv
. .venv/bin/activate
python -m pip install -r requirements.txt
ansible-galaxy collection install -r requirements.yml

mkdir -p inventories/local
cp inventories/lab/hosts.yml inventories/local/hosts.yml
```

Replace the sample documentation addresses with lab management addresses and add verified SSH host keys to the controller's known-hosts file. SSH plays use Ansible's normal SSH credentials. Prefer a restricted account and SSH key, or use `-u netops -k` with password authentication. Some Cisco outputs require privileged EXEC. Supply enable credentials with Vault where authorized.

For API plays, populate the relevant environment variables through your secret manager.

| Platform | Credentials | Target |
| --- | --- | --- |
| FortiGate | `FORTIOS_TOKEN` | FortiGate management address with the intended `fortios_vdom` and a read-only token |
| Check Point | `CHECKPOINT_USERNAME`, `CHECKPOINT_PASSWORD` | Management server with read-only API access in the intended domain |
| PAN-OS | `PANOS_API_KEY` | Firewall management address with restricted API access and the intended `panos_vsys` |

FortiGate and Check Point inventory defaults request HTTPS certificate validation. PAN-OS uses the vendor SDK transport. Review its certificate behavior for your installed version before using it beyond an isolated management network. Never commit credentials or live reports.

## First run

```bash
ansible-playbook cisco-ios/system_inventory.yml --syntax-check
ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml --list-hosts --limit ios-lab
ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml --limit ios-lab
```

The IOS inventory workflow collects software and hardware information. Other starting points include the [NX-OS vPC check](cisco-nx-os/vpc_peer_health.yml), [FortiGate policy audit](fortigate-fortios/firewall_policy_audit.yml) and [PAN-OS IPsec check](palo-alto-pan-os/ipsec_health.yml).

## Reports and comparisons

- Reports land in `artifacts/`, or set `report_root` to an absolute path. Each run gets a unique filename.
- Partial reports retain successful queries and identify the failed queries. The play fails for that host so incomplete collection is visible.
- Reports contain raw device evidence. File permissions are restricted, but output can still contain credentials, configuration and topology. Store it on an approved controller.
- Check Point inventories retrieve a single configurable page per object class. Use the pagination metadata and override `checkpoint_offset` for later pages.

Compare two complete snapshots collected for the same workflow and inventory alias. Raw changes can include volatile counters or timestamps.

```bash
ansible-playbook ops/compare-reports.yml \
  -e baseline_path=/absolute/path/baseline.json \
  -e current_path=/absolute/path/current.json \
  -e fail_on_drift=true
```

## Operator reference

See [Everyday Ansible commands](docs/daily-commands.md) for inventory, target limits, module discovery, Vault and SSH checks.

The platform folders link every playbook to the queries it runs. Hardware and software features vary. Start on a lab target matching the platform notes. The published playbooks have been checked as YAML and structurally verified. Live validation remains device- and release-specific.

### Vendor references

- [Cisco IOS command module](https://docs.ansible.com/projects/ansible/latest/collections/cisco/ios/ios_command_module.html) and [Cisco NX-OS command module](https://docs.ansible.com/projects/ansible/latest/collections/cisco/nxos/nxos_command_module.html)
- [Junos platform options](https://docs.ansible.com/projects/ansible/latest/network/user_guide/platform_junos.html) and [AOS-CX collection](https://github.com/aruba/aoscx-ansible-collection)
- [FortiOS configuration facts](https://docs.ansible.com/projects/ansible/latest/collections/fortinet/fortios/fortios_configuration_fact_module.html), [Check Point Management collection](https://docs.ansible.com/projects/ansible/latest/collections/check_point/mgmt/index.html) and [PAN-OS operational module](https://github.com/PaloAltoNetworks/pan-os-ansible/blob/develop/plugins/modules/panos_op.py)
