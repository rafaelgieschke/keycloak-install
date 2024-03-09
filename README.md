## Run via cloud-init

```
#!/usr/bin/env -S -- sh -c 'git clone --recursive "$0"; cd "${0##*/}" && ./user-data' https://github.com/rafaelgieschke/keycloak-install
```

<!--
```
#!/usr/bin/env -S -- sh -c 'curl -fL "$0" | sh' https://github.com/rafaelgieschke/keycloak-install/raw/keycloak-caddy/user-data
```
-->

<!--
```
#!/bin/sh
run() { git clone --recursive "$1"; cd "${1##*/}" && ./user-data; }
run https://github.com/rafaelgieschke/keycloak-install
```
-->

```
#!/bin/sh -xeu
type git || apt-get update && apt-get install -y git
run() (set -- "$1" "${1%%/blob/*}"; set -- "$2" "${1#$2/blob/}";
git clone --recursive -b "${2%%/*}" -- "$1" || :; cd -- "${1##*/}" && "./${2#*/}")

run https://github.com/rafaelgieschke/keycloak-install/blob/main/user-data
```

### Export realm

```
sudo compose stop /keycloak-install
sudo compose docker /keycloak-install run keycloak export --file /opt/keycloak/data/h2/keycloak.json
sudo compose restart /keycloak-install
```
