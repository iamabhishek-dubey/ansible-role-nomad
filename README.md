## Ansible Role: Nomad

Ansible role to setup, manage nomad cluster/standalone

Some of the highlighting features are:-

  - Cluster and Standalone setup of Nomad cluster
  - Nomad server and client support
  - Windows support (In development)
  - Healthcheck integration for nomad

This role supports Debian family right now, other OS support is under construction.

### Requirements

**No third party requirement is needed by this role**

### Roles Variables

Roles variables are categorized into two divisions i.e. Mandatory and Optional.

#### Mandatory Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| nomad_data_dir | `/opt/nomad` | `Linux path` | string | Data directory for nomad node |
| nomad_config_dir | `/etc/nomad.d` | `Linux path` | string | Configuration directory for nomad node |
| nomad_datacenter | `new-jersey-primary` | `Any name` | string | Name of the datacenter for nomad nodes |

#### Optional Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| nomad_version | `0.12.9` | `Nomad version` | string | Nomad version which needs to be installed |


### Usage

The inventory for nomad role should look like this:-

```ini
[nomad:children]
nomad_server
nomad_client

[nomad_server]
nomad-server1 ansible_ssh_host=54.201.236.237
nomad-server2 ansible_ssh_host=54.149.235.249
nomad-server3 ansible_ssh_host=34.221.65.129

[nomad_client]
nomad-client1 ansible_ssh_host=54.200.248.248

[nomad:vars]
ansible_ssh_user=ubuntu
ansible_ssh_common_args='-o StrictHostKeyChecking=no'
```

and for running the ansible role, we will use ansible cli.

```shell
ansible-playbook -i tests/inventory tests/test.yml
```
