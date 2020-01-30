# Jormungandr Ansible Role

Installs Jormungandr for Ubuntu Bionic.

## Requirements

None.

## Role Variables

Three variables are required for the `node_secret.yaml` file:

- `node_sig_key`
- `node_vrf_key`
- `node_pool_id`

These values will have been created when creating the stake pool.

The following variables are also availble with defaults:

    binary_base_url: https://github.com/input-output-hk/jormungandr/releases/download
    binary_version: 0.8.8
    binary_match: "jormungandr {{ binary_version }}$"
    jormungandr_user: cardano
    jormungandr_storage_dir: "/home/{{ jormungandr_user }}/storage"
    jormungandr_rest_port: 3001
    jormungandr_public_address_port: 3000
    Jormungandr_log_level: warn
    jormungandr_max_unreachable_nodes_to_connect_per_event: 128
    genesis_block_hash: 8e4d2a343f3dcf9330ad9035b3e8d168e6728904262f2c434a4f8f934ec7b676 

It is also possible to provide a list of trusted peers in the following format:

    trusted_peers:
      - address: ...
        id: ...
      - address: ...
        id: ...

For the default values refer to `defaults/main.yml`.

## Dependencies

None.

## Example Playbook

    - hosts: all
      tasks:
        - name: Setup Jormungandr
          include_role:
            name: Jormungandr-Ansible-Role
          vars:
            node_sig_key: kes25519-12...
            node_vrf_key: vrf_...
            node_pool_id: c158...

## License

MIT
