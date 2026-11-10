# Juniper Junos

Enable NETCONF on the target and allow TCP 830. Apply MPLS, IS-IS and Virtual Chassis workflows only to supported nodes.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml juniper-junos/chassis_inventory.yml --limit junos-lab
```

| Playbook | Queries collected |
| --- | --- |
| [Chassis inventory](chassis_inventory.yml) | `show version`<br>`show chassis hardware` |
| [Alarm review](alarm_review.yml) | `show system alarms`<br>`show chassis alarms` |
| [Routing engine health](routing_engine_health.yml) | `show chassis routing-engine`<br>`show system processes extensive` |
| [Storage and cores](storage_and_cores.yml) | `show system storage`<br>`show system core-dumps` |
| [Commit history](commit_history.yml) | `show system commit` |
| [Virtual chassis health](virtual_chassis_health.yml) | `show virtual-chassis status` |
| [Interface health](interface_health.yml) | `show interfaces terse`<br>`show interfaces descriptions` |
| [Optics review](optics_review.yml) | `show interfaces diagnostics optics` |
| [Neighbor discovery](neighbor_discovery.yml) | `show lldp neighbors detail` |
| [Switching table](switching_table.yml) | `show ethernet-switching table` |
| [Vlan membership](vlan_membership.yml) | `show vlans` |
| [Spanning tree health](spanning_tree_health.yml) | `show spanning-tree bridge`<br>`show spanning-tree interface` |
| [Lacp health](lacp_health.yml) | `show lacp interfaces` |
| [Rib review](rib_review.yml) | `show route summary`<br>`show route instance` |
| [Hidden route triage](hidden_route_triage.yml) | `show route hidden extensive` |
| [Bgp peer review](bgp_peer_review.yml) | `show bgp summary` |
| [Ospf adjacencies](ospf_adjacencies.yml) | `show ospf neighbor detail` |
| [Isis adjacencies](isis_adjacencies.yml) | `show isis adjacency detail` |
| [Mpls lsp health](mpls_lsp_health.yml) | `show mpls lsp extensive` |
| [Configuration backup](configuration_backup.yml) | `show configuration` |
