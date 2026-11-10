# Palo Alto PAN-OS

Target the firewall management API with a read-only API key. Classic routing workflows require the classic routing engine. PAN-OS transport follows the PAN-OS Python SDK TLS behavior. Use a trusted isolated management network.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml palo-alto-pan-os/system_inventory.yml --limit panos-lab
```

| Playbook | Queries collected |
| --- | --- |
| [System inventory](system_inventory.yml) | `show system info` |
| [Management plane health](management_plane_health.yml) | `show system resources`<br>`show system disk-space` |
| [Management process health](management_process_health.yml) | `show system software status` |
| [Commit job review](commit_job_review.yml) | `show jobs all` |
| [Panorama connectivity](panorama_connectivity.yml) | `show panorama-status` |
| [Ha state](ha_state.yml) | `show high-availability state`<br>`show high-availability state-synchronization` |
| [Ha monitoring](ha_monitoring.yml) | `show high-availability link-monitoring`<br>`show high-availability path-monitoring` |
| [Interface inventory](interface_inventory.yml) | `show interface all` |
| [Interface error review](interface_error_review.yml) | `show counter interface all` |
| [Arp and lldp](arp_and_lldp.yml) | `show arp all`<br>`show lldp neighbors all` |
| [Classic route review](classic_route_review.yml) | `show routing route`<br>`show routing fib` |
| [Classic bgp review](classic_bgp_review.yml) | `show routing protocol bgp summary` |
| [Classic ospf review](classic_ospf_review.yml) | `show routing protocol ospf neighbor` |
| [Security policy audit](security_policy_audit.yml) | `show running security-policy` |
| [Nat policy audit](nat_policy_audit.yml) | `show running nat-policy` |
| [Session capacity](session_capacity.yml) | `show session info` |
| [Ipsec health](ipsec_health.yml) | `show vpn ike-sa`<br>`show vpn ipsec-sa` |
| [Vpn dataplane review](vpn_dataplane_review.yml) | `show vpn flow` |
| [Dataplane resource review](dataplane_resource_review.yml) | `show running resource-monitor` |
| [Drop counter review](drop_counter_review.yml) | `show counter global filter severity drop` |
