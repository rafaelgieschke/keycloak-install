## Run via cloud-init

```
#!/usr/bin/env -S -- sh -c 'curl -fL "$0" | sh' https://github.com/rafaelgieschke/keycloak-install/raw/keycloak-caddy/user-data
```

<!--
#!/usr/bin/env -S -- sh -c 'git clone "$0" && cd "${0##*/}" && ./user-data' https://github.com/rafaelgieschke/keycloak-install
-->
