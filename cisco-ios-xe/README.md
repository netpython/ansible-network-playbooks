# Cisco IOS XE

Use a supported Catalyst switch for StackWise and FED workflows. Use a QFP-based router for QFP workflows. Run model-specific workflows against the applicable inventory subset.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml cisco-ios-xe/platform_inventory.yml --limit ios_xe-lab
```

| Playbook | Queries collected |
| --- | --- |
| [Platform inventory](platform_inventory.yml) | `show version`<br>`show platform`<br>`show inventory` |
| [Control plane health](control_plane_health.yml) | `show platform software status control-processor brief`<br>`show processes cpu platform sorted` |
| [Software install state](software_install_state.yml) | `show install summary`<br>`show boot` |
| [License review](license_review.yml) | `show license summary`<br>`show license status` |
| [Stackwise health](stackwise_health.yml) | `show switch`<br>`show switch stack-ports summary` |
| [Optics review](optics_review.yml) | `show interfaces transceiver detail` |
| [Physical error triage](physical_error_triage.yml) | `show interfaces status`<br>`show interfaces counters errors` |
| [Trunk validation](trunk_validation.yml) | `show interfaces trunk`<br>`show etherchannel summary` |
| [Spanning tree health](spanning_tree_health.yml) | `show spanning-tree summary`<br>`show spanning-tree inconsistentports` |
| [Poe capacity](poe_capacity.yml) | `show power inline` |
| [Access authentication](access_authentication.yml) | `show authentication sessions` |
| [First hop security](first_hop_security.yml) | `show ip dhcp snooping binding`<br>`show ip arp inspection statistics` |
| [Vrf inventory](vrf_inventory.yml) | `show vrf` |
| [Ospf and bfd](ospf_and_bfd.yml) | `show ip ospf neighbor`<br>`show bfd neighbors details` |
| [Bgp peer review](bgp_peer_review.yml) | `show bgp ipv4 unicast summary` |
| [Ipsec health](ipsec_health.yml) | `show crypto ikev2 sa`<br>`show crypto ipsec sa` |
| [Qfp datapath triage](qfp_datapath_triage.yml) | `show platform hardware qfp active datapath utilization`<br>`show platform hardware qfp active statistics drop` |
| [Catalyst punt triage](catalyst_punt_triage.yml) | `show platform software fed switch active punt cause summary` |
| [Quality of service](quality_of_service.yml) | `show policy-map interface` |
| [Configuration backup](configuration_backup.yml) | `show running-config` |
