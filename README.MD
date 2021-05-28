# nemesis.whalewave.net

## Setup the vultr.ini file

---

The Nemesis project leverage [Vultr](https://www.vultr.com) as a VPS provider. This requires a working API key. That key must be inserted into the `vultr.ini` file.

```
[default]
key = [REDACTED]
timeout = 60
```

## Define an inventory

---

The `inventory.ini` file defines how many VPS should be created on [Vultr](https://www.vultr.com). 

```
[vultr_servers]
debian.whalewave.net
```

This will automatically create a new VPS on vultr and a subdomain throught [Cloudflare](https://www.cloudflare.com/) API when running the playbook.

## Run the playbook

---

The following snippet will run the playbook that will bootstrap servers and provision them with Ansible. It requires a [Cloudflare](https://www.cloudflare.com/) API key and a [vault.whalewave.net](http://vault.whalewave.net) token. 

```
ansible-playbook playbook.yml --user shellwhale --inventory inventory.ini --extra-vars "cloudflare_api_key=[REDACTED] vault_token=[REDACTED]"
```
