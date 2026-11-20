# Capture DHCPv4 server evidence

Use this workflow on a lab IOS router acting as the DHCP server. It is not a remote query of a server behind an IOS relay, nor a DHCP snooping audit.

## Requirements and inventory

Use the repository's Linux controller setup and collections `cisco.ios` and `ansible.netcommon` from [requirements.yml](../requirements.yml). The existing [sample inventory](../inventories/lab/hosts.yml) defines group `ios`, alias `ios-lab`, documentation address 192.0.2.11, `network_cli` and `cisco.ios.ios`.

Copy that inventory to `inventories/local/hosts.yml`, replace the address, and verify the device SSH host key. Use a restricted account authorized for the four show commands; supply secrets via your SSH/Vault setup, never in Git. Do not disable host-key verification.

## Run from the repository root

```bash
ansible-playbook -i inventories/local/hosts.yml cisco-ios/dhcp_server_audit.yml --syntax-check
ansible-playbook -i inventories/local/hosts.yml cisco-ios/dhcp_server_audit.yml --list-hosts --limit ios-lab
ansible-playbook -i inventories/local/hosts.yml cisco-ios/dhcp_server_audit.yml --limit ios-lab -u netops -k
```

The shared collector writes a unique, restricted JSON file under `artifacts/`, or an absolute directory passed through `-e report_root=/approved/path`. It retains raw output per query. A failed query leaves a partial report and fails the host instead of declaring success.

## Interpret the evidence

Compare pools, bindings, recorded conflicts and message counts with a known client attempt. These are observations, not an automatic health verdict. Timestamp two captures if studying activity. An empty binding table can be legitimate; a conflict needs investigation before any release or clearing operation.

No configuration or clear command is issued. Reports can contain client identifiers and addresses: keep them outside version control. Large binding tables can produce substantial output.

The shared collector explicitly ends the host in check mode. Therefore `--check` does not collect or validate DHCP state; use `--syntax-check` only for static Ansible validation.

## Validation boundary

YAML structure and collector integration can be verified offline. Live SSH, device-specific command support and actual DHCP behavior require a licensed IOS/IOS XE lab image; no live test is claimed.

Sources: [IOS DHCP server verification](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_dhcp/configuration/12-4/dhcp-12-4-book/config-dhcp-server.html), [cisco.ios.ios_command](https://docs.ansible.com/projects/ansible/latest/collections/cisco/ios/ios_command_module.html).
