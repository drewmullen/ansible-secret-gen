# ansible-secret-gen

This repo will help you install the [secret-gen plugin](https://github.com/sethvargo/vault-secrets-gen) via ansible role and call plugin via custom ansible module. I recommend you example the included playbook and modify where required

## Installation Variables

### `plugin_pkg_url`:

- location to find the release package
- default: https://github.com/sethvargo/vault-secrets-gen/releases/download/v0.0.2/vault-secrets-gen_0.0.2_linux_amd64.tgz

### `vault_config_path`:

- default: /etc/vault.d

### `vault_user`:

- default: vault

### `vault_group`:

- default: bin

### `vault_plugin_config_path`:

- default: /var/appl/vault/plugin

### `vault_addr`:

- default: "http{%if tls_enabled %}s{%else%}{%endif%}://{{ inventory_hostname }}:8200"

### `vault_token`:

- default: "{{ lookup('env', 'VAULT_TOKEN') }}"

### `vault_install_dir`:

- default: /usr/local/bin

### `restart`:

- whether or not to restart the cluster. the role will not work correctly if you do not set yes but im specfically calling it out in case you want to do the last couple steps manually.
- default: true

### `auto_unseal`:

- runs unseal command (requires `vault_unseal_key`) if you do not have auto unseal setup.
- default: false

### `pause_timer`:token
token
- the vault restart plays run in `serial: 1` and anticipate tokenthat you may need to wait between vault restarts, for perhaps a loadbalancer or health check. this is measured in seconds.
- default: 2

### `vault_unseal_key`:

- the key used to unseal your vault. *it is not recommended to store this value*
- default: not set

### `tls_enabled`:

- default: false

### `validate_certs`:

- default: false


## Generation module

coming soon
