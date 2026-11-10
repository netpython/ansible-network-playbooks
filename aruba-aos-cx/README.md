# Aruba AOS-CX

Use the AOS-CX SSH CLI. Apply VSX, BGP, PoE and port access workflows only to compatible switch models and roles.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml aruba-aos-cx/system_inventory.yml --limit aruba-lab
```

| Playbook | Queries collected |
| --- | --- |
| [System inventory](system_inventory.yml) | `show version`<br>`show system`<br>`show inventory` |
| [Boot and image review](boot_and_image_review.yml) | `show images`<br>`show boot-history` |
| [Environmental health](environmental_health.yml) | `show environment fan`<br>`show environment power-supply`<br>`show environment temperature` |
| [Capacity review](capacity_review.yml) | `show capacities`<br>`show capacities-status` |
| [Clock and ntp](clock_and_ntp.yml) | `show clock`<br>`show ntp status`<br>`show ntp associations` |
| [Interface inventory](interface_inventory.yml) | `show interface brief`<br>`show ip interface brief` |
| [Optics review](optics_review.yml) | `show interface transceiver detail` |
| [Vlan membership](vlan_membership.yml) | `show vlan` |
| [Mac learning](mac_learning.yml) | `show mac-address-table` |
| [Neighbor discovery](neighbor_discovery.yml) | `show lldp neighbor-info` |
| [Lacp health](lacp_health.yml) | `show lacp interfaces`<br>`show lacp aggregates` |
| [Spanning tree health](spanning_tree_health.yml) | `show spanning-tree detail` |
| [Poe audit](poe_audit.yml) | `show power-over-ethernet brief` |
| [Port access audit](port_access_audit.yml) | `show port-access clients` |
| [Vrf routing](vrf_routing.yml) | `show vrf`<br>`show ip route` |
| [Ospf adjacencies](ospf_adjacencies.yml) | `show ip ospf neighbors` |
| [Bgp peer review](bgp_peer_review.yml) | `show bgp ipv4 unicast summary` |
| [Vsx pair health](vsx_pair_health.yml) | `show vsx status` |
| [Vrrp health](vrrp_health.yml) | `show vrrp` |
| [Configuration backup](configuration_backup.yml) | `show running-config` |
