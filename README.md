# Ubuntu installer

My ubuntu i3-gaps installer

```bash
sudo apt update \
&& sudo DEBIAN_FRONTEND=noninteractive NEEDRESTART_MODE=a apt full-upgrade -y \
&& sudo apt install ansible -y \
&& mkdir -p .gc \
&& cd .gc \
&& git clone https://github.com/pietryszak/ubuntu-installer \
&& cd ubuntu-installer \
&& ansible-playbook --ask-become-pass --connection=local --inventory 127.0.0.1, playbook.yml
```

Cups - printer panel accesible from browser
http://localhost:631/ 
