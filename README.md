# Ubuntu installer

My ubuntu i3-gaps installer


### When installed on host

```bash
sudo apt update \
&& sudo DEBIAN_FRONTEND=noninteractive apt full-upgrade -y \
&& sudo DEBIAN_FRONTEND=noninteractive apt install ansible -y \
&& mkdir -p .gc \
&& cd .gc \
&& git clone https://github.com/pietryszak/ubuntu-installer \
&& cd ubuntu-installer \
&& ansible-playbook --ask-become-pass --connection=local --inventory 127.0.0.1, all.yml \
&& ansible-playbook --ask-become-pass --connection=local --inventory 127.0.0.1, host.yml
```

Cups - printer panel accesible from browser
http://localhost:631/ 

---
### When installed on virtualbox

```bash
sudo apt update \
&& sudo DEBIAN_FRONTEND=noninteractive apt full-upgrade -y \
&& sudo DEBIAN_FRONTEND=noninteractive apt install ansible -y \
&& mkdir -p .gc \
&& cd .gc \
&& git clone https://github.com/pietryszak/ubuntu-installer \
&& cd ubuntu-installer \
&& ansible-playbook --ask-become-pass --connection=local --inventory 127.0.0.1, all.yml \
&& ansible-playbook --ask-become-pass --connection=local --inventory 127.0.0.1, virtualbox.yml
```


