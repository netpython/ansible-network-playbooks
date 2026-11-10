# Everyday Ansible commands for network operations

Run these commands from the repository root. Replace `ios-lab` with the intended inventory alias.

| Task | Command |
| --- | --- |
| Show effective settings | `ansible-config dump --only-changed` |
| List installed collections | `ansible-galaxy collection list` |
| Read module arguments | `ansible-doc cisco.ios.ios_command` |
| Inspect group membership | `ansible-inventory -i inventories/local/hosts.yml --graph` |
| Resolve target aliases | `ansible ios -i inventories/local/hosts.yml --list-hosts` |
| Check playbook syntax | `ansible-playbook cisco-ios/system_inventory.yml --syntax-check` |
| Preview exactly which hosts will be targeted | `ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml --list-hosts --limit ios-lab` |
| List tasks in the play | `ansible-playbook cisco-ios/system_inventory.yml --list-tasks` |
| Run against a pilot device | `ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml --limit ios-lab` |
| Prompt for the SSH password | `ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml -u netops -k --limit ios-lab` |
| Reduce controller concurrency | `ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml -f 2` |
| Validate an IOS SSH path | `ansible ios -i inventories/local/hosts.yml -m cisco.ios.ios_command -a '{"commands":["show clock"]}' --limit ios-lab` |
| Create an encrypted vars file | `ansible-vault create inventories/local/credentials.yml` |
| Edit an encrypted vars file | `ansible-vault edit inventories/local/credentials.yml` |
| Run with Vault variables | `ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml -e @inventories/local/credentials.yml --ask-vault-pass --limit ios-lab` |

Use `--list-hosts` first when changing an inventory or limit expression. These collectors skip device queries in `--check` mode. Use a one-device read-only run to verify connectivity. The built-in Ansible `ping` module checks Python on a managed host and is generally unsuitable for network appliances.

`-vvv` can help investigate connection setup. Treat verbose output as sensitive and avoid persistent connection logging with live credentials.
