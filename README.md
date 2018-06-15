# Ansible-network_key_chain

Ansible role that configures key chains on network devices.  

The configuration of the role is done so that it shouldn't be necessary to modify the role for any configuration.
All settings can be configured by changing role parameters or by declaring new config as variable.

Please report any issues or send PR.

## Examples

```yaml
---
- name: Example of how to create a couple key chains, one having a key and one 2 keys
  hosts: switches
  vars:
    key_chains:
      hsrp:
        state: present
        key_ids:
          - key_id: 1
            key_string: test
          - key_id: 2
            key_string: test2
      ospf:
        state: present
        key_ids:
          - key_id: 1
            key_string: 7 071b245f5a
  roles:
    - Ansible-network_key_chain

- name: Example of how to delete a key chain. Deletes the whole key chain so all keys in the chain.
  hosts: switches
  vars:
    key_chains:  
      ospf:
        state: absent
  roles:
    - Ansible-network_key_chain

```

## Role variables

```yaml
---
# Define the key chains to be configured (see README for examples)
 key_chains: { }
```


## License

Apache


## Author

Dan Murarasu
