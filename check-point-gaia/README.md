# Check Point Management API

Target the Check Point management server and correct API domain. These workflows read one page per object class (default 50). Inspect the returned pagination metadata and pass checkpoint_offset to request later pages. The folder does not SSH to Gaia gateways.

Run from the repository root after following [setup](../README.md#setup).

```bash
ansible-playbook -i inventories/local/hosts.yml check-point-gaia/management_package_inventory.yml --limit checkpoint-lab
```

| Playbook | Queries collected |
| --- | --- |
| [Management package inventory](management_package_inventory.yml) | `package` |
| [Access layer inventory](access_layer_inventory.yml) | `access_layer` |
| [Host object inventory](host_object_inventory.yml) | `host` |
| [Network object inventory](network_object_inventory.yml) | `network` |
| [Address range inventory](address_range_inventory.yml) | `address_range` |
| [Group object inventory](group_object_inventory.yml) | `group` |
| [Tcp service inventory](tcp_service_inventory.yml) | `service_tcp` |
| [Udp service inventory](udp_service_inventory.yml) | `service_udp` |
| [Icmp service inventory](icmp_service_inventory.yml) | `service_icmp` |
| [Service group inventory](service_group_inventory.yml) | `service_group` |
| [Time object inventory](time_object_inventory.yml) | `time` |
| [Security zone inventory](security_zone_inventory.yml) | `security_zone` |
| [Dynamic object inventory](dynamic_object_inventory.yml) | `dynamic_object` |
| [Application site inventory](application_site_inventory.yml) | `application_site` |
| [Application site group inventory](application_site_group_inventory.yml) | `application_site_group` |
| [Access role inventory](access_role_inventory.yml) | `access_role` |
| [Simple gateway inventory](simple_gateway_inventory.yml) | `simple_gateway` |
| [Simple cluster inventory](simple_cluster_inventory.yml) | `simple_cluster` |
| [Network object dependency snapshot](network_object_dependency_snapshot.yml) | `host`<br>`network`<br>`address_range`<br>`group` |
| [Service dependency snapshot](service_dependency_snapshot.yml) | `service_tcp`<br>`service_udp`<br>`service_icmp`<br>`service_group` |
