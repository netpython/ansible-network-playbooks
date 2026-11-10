# Cisco NX-OS

Use Nexus 9000 and limit feature-specific workflows to devices with the relevant protocol enabled.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml cisco-nx-os/chassis_inventory.yml --limit nx_os-lab
```

| Playbook | Queries collected |
| --- | --- |
| [Chassis inventory](chassis_inventory.yml) | `show version`<br>`show inventory`<br>`show module` |
| [System health](system_health.yml) | `show system resources`<br>`show environment` |
| [Event review](event_review.yml) | `show logging last 50`<br>`show cores` |
| [Time sync](time_sync.yml) | `show clock`<br>`show ntp peers` |
| [Feature audit](feature_audit.yml) | `show feature` |
| [Interface error triage](interface_error_triage.yml) | `show interface brief`<br>`show interface counters errors` |
| [Optics review](optics_review.yml) | `show interface transceiver details` |
| [Vlan and trunk audit](vlan_and_trunk_audit.yml) | `show vlan brief`<br>`show interface trunk` |
| [Mac learning](mac_learning.yml) | `show mac address-table dynamic` |
| [Lacp health](lacp_health.yml) | `show port-channel summary`<br>`show lacp neighbor` |
| [Vpc peer health](vpc_peer_health.yml) | `show vpc brief`<br>`show vpc peer-keepalive` |
| [Vpc consistency](vpc_consistency.yml) | `show vpc consistency-parameters global` |
| [Spanning tree health](spanning_tree_health.yml) | `show spanning-tree summary`<br>`show spanning-tree inconsistentports` |
| [Vrf routing](vrf_routing.yml) | `show vrf`<br>`show ip route vrf all` |
| [Ospf adjacencies](ospf_adjacencies.yml) | `show ip ospf neighbors` |
| [Ipv4 bgp summary](ipv4_bgp_summary.yml) | `show bgp ipv4 unicast summary` |
| [Evpn route review](evpn_route_review.yml) | `show bgp l2vpn evpn summary`<br>`show bgp l2vpn evpn route-type 2` |
| [Vxlan overlay health](vxlan_overlay_health.yml) | `show nve peers`<br>`show nve vni` |
| [Bfd and hsrp](bfd_and_hsrp.yml) | `show bfd neighbors`<br>`show hsrp brief` |
| [Configuration backup](configuration_backup.yml) | `show running-config` |
