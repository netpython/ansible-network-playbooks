# FortiGate / FortiOS

Use a read-only REST API token scoped to the target VDOM. These queries audit configured objects and are not a live routing or session view. Feature availability varies by release.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml fortigate-fortios/interface_inventory.yml --limit fortios-lab
```

| Playbook | Queries collected |
| --- | --- |
| [Interface inventory](interface_inventory.yml) | `system_interface` |
| [Zone membership](zone_membership.yml) | `system_zone` |
| [Static route audit](static_route_audit.yml) | `router_static` |
| [Policy route audit](policy_route_audit.yml) | `router_policy` |
| [Bgp configuration review](bgp_configuration_review.yml) | `router_bgp` |
| [Ospf configuration review](ospf_configuration_review.yml) | `router_ospf` |
| [Sdwan configuration review](sdwan_configuration_review.yml) | `system_sdwan` |
| [Firewall policy audit](firewall_policy_audit.yml) | `firewall_policy` |
| [Address inventory](address_inventory.yml) | `firewall_address` |
| [Address group audit](address_group_audit.yml) | `firewall_addrgrp` |
| [Custom service audit](custom_service_audit.yml) | `firewall.service_custom` |
| [Service group audit](service_group_audit.yml) | `firewall.service_group` |
| [Destination nat audit](destination_nat_audit.yml) | `firewall_vip` |
| [Source nat pool audit](source_nat_pool_audit.yml) | `firewall_ippool` |
| [Central snat audit](central_snat_audit.yml) | `firewall_central-snat-map` |
| [Dhcp server audit](dhcp_server_audit.yml) | `system.dhcp_server` |
| [Ipsec phase1 audit](ipsec_phase1_audit.yml) | `vpn.ipsec_phase1-interface` |
| [Ipsec phase2 audit](ipsec_phase2_audit.yml) | `vpn.ipsec_phase2-interface` |
| [Administrator profiles](administrator_profiles.yml) | `system_accprofile` |
| [Policy dependency snapshot](policy_dependency_snapshot.yml) | `firewall_policy`<br>`firewall_address`<br>`firewall_addrgrp`<br>`firewall.service_custom`<br>`firewall.service_group` |
