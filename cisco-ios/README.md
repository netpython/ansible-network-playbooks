# Cisco IOS

Use a Catalyst switch for campus switching workflows and supported IOS routers for routing and NAT workflows.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml cisco-ios/system_inventory.yml --limit ios-lab
```

| Playbook | Queries collected |
| --- | --- |
| [System inventory](system_inventory.yml) | `show version`<br>`show inventory` |
| [Cpu triage](cpu_triage.yml) | `show processes cpu sorted` |
| [Memory triage](memory_triage.yml) | `show processes memory sorted` |
| [Event review](event_review.yml) | `show logging` |
| [Clock and ntp](clock_and_ntp.yml) | `show clock detail`<br>`show ntp associations` |
| [Interface health](interface_health.yml) | `show ip interface brief`<br>`show interfaces` |
| [Switchport errors](switchport_errors.yml) | `show interfaces status`<br>`show interfaces counters errors` |
| [Vlan membership](vlan_membership.yml) | `show vlan brief` |
| [Trunk validation](trunk_validation.yml) | `show interfaces trunk`<br>`show vlan brief` |
| [Mac learning](mac_learning.yml) | `show mac address-table dynamic` |
| [Etherchannel health](etherchannel_health.yml) | `show etherchannel summary`<br>`show lacp neighbor` |
| [Spanning tree health](spanning_tree_health.yml) | `show spanning-tree summary`<br>`show spanning-tree inconsistentports` |
| [Neighbor discovery](neighbor_discovery.yml) | `show cdp neighbors detail`<br>`show lldp neighbors detail` |
| [Poe audit](poe_audit.yml) | `show power inline` |
| [Ipv4 routing](ipv4_routing.yml) | `show ip route`<br>`show ip protocols` |
| [Ospf adjacencies](ospf_adjacencies.yml) | `show ip ospf neighbor`<br>`show ip ospf interface brief` |
| [Bgp peer review](bgp_peer_review.yml) | `show ip bgp summary` |
| [Eigrp convergence](eigrp_convergence.yml) | `show ip eigrp neighbors`<br>`show ip eigrp topology` |
| [Nat health](nat_health.yml) | `show ip nat statistics`<br>`show ip nat translations` |
| [Configuration backup](configuration_backup.yml) | `show running-config` |
