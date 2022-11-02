# Ubuntu installer

My ubuntu i3-gaps installer
---

### When installed on host

```bash
sudo apt update \
&& sudo DEBIAN_FRONTEND=noninteractive apt full-upgrade -y \
&& sudo DEBIAN_FRONTEND=noninteractive apt install ansible -y \
&& mkdir -p ~/.gc \
&& cd ~/.gc \
&& git clone https://github.com/pietryszak/ubuntu-installer \
&& cd ubuntu-installer \
&& ansible-playbook --ask-become-pass --connection=local --inventory 127.0.0.1, all.yml host.yml
```

Cups - printer panel accesible from browser
http://localhost:631/ 

### After installation you can add/remove extra futures:

* Gammastep - Blue light remover 

[Gammastep](https://gitlab.com/chinstrap/gammastep) adjusts the color temperature of your screen according to your surroundings. This may help your eyes hurt less if you are working in front of the screen at night. You can add your location to RedShift.

To take yours location use script:
```bash
curl -s "https://location.services.mozilla.com/v1/geolocate?key=geoclue" | jq '.location.lat, .location.lng'
```

To add yours location to Redshift use this script:
```bash
sed -i -e '/lat/s/52.23/FIRST VALUE OF SCRIPT/' ~/.config/gammastep/config.ini
sed -i -e '/lon/s/21.01/SECOND VALUE OF SCRIPT/' ~/.config/gammastep/config.ini
```

*  OpenWeader in Polybar 

In right side of polybar is small arrow, after click it an additionall bar shows a few information included a weather. To use it, you need to add OpenWeather API.
Create an API key in [OpenWeatherMap](https://home.openweathermap.org)

```bash
sed -i 's/KEY=""/KEY="YOUR_API_KEY_HERE"/g' ~/.config/polybar/scripts/openweathermap-fullfeatured.sh
```

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
&& ansible-playbook --ask-become-pass --connection=local --inventory 127.0.0.1, all.yml virtualbox.yml
```

---

If you not need polish date and time format in system just use this script
```bash
sudo sed -i 's/LC_NUMERIC="pl_PL.UTF-8"/#LC_NUMERIC="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_TIME="pl_PL.UTF-8"/#LC_TIME="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_MONETARY="pl_PL.UTF-8"/#LC_MONETARY="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_PAPER="pl_PL.UTF-8"/#LC_PAPER="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_NAME="pl_PL.UTF-8"/#LC_NAME="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_ADDRESS="pl_PL.UTF-8"/#LC_ADDRESS="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_TELEPHONE="pl_PL.UTF-8"/#LC_TELEPHONE="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_MEASUREMENT="pl_PL.UTF-8"/#LC_MEASUREMENT="pl_PL.UTF-8"/g' /etc/default/locale
sudo sed -i 's/LC_IDENTIFICATION="pl_PL.UTF-8"/#LC_IDENTIFICATION="pl_PL.UTF-8"/g' /etc/default/locale
```