## Run via cloud-init

```
#!/usr/bin/env -S -- sh -c 'git clone --recursive "$0"; cd "${0##*/}" && ./user-data' https://github.com/rafaelgieschke/keycloak-install
```

<!--
```
#!/usr/bin/env -S -- sh -c 'curl -fL "$0" | sh' https://github.com/rafaelgieschke/keycloak-install/raw/keycloak-caddy/user-data
```
-->


### Export realm

```
sudo compose stop /keycloak-install
sudo compose docker /keycloak-install run keycloak export --file /opt/keycloak/data/h2/keycloak.json
sudo compose restart /keycloak-install
```
