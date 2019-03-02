# ha_on_rspi
## debian install homeassistant 

#### debian add python3.7 testing
>sudo nano /etc/apt/sources.list
#### add tsinghua testing 
```
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ testing main
```

>echo 'APT::Default-Release "stable";' | sudo tee -a /etc/apt/apt.conf.d/00local

#### update testing
>sudo apt update
#### install python3.7
>sudo apt -t testing install python3.7 python3-pip python3-dev python3-setuptools python3-distutils

>sudo pip3 install wheel

>sudo pip3 install pqi

>sudo pqi use tuna

>pqi use tuna

#### install homeassistant
>sudo pip3 install homeassistant

#### create autostart file
>sudo nano -w /etc/systemd/system/home-assistant.service

```
[Unit]
Description=Home Assistant
After=network-online.target

[Service]
Type=simple
User=%i
ExecStart=/usr/local/bin/hass

[Install]
WantedBy=multi-user.target
```
#### reload systemctl
>sudo systemctl --system daemon-reload

#### enable autostart
>sudo systemctl enable home-assistant

#### run!
>sudo systemctl start home-assistant
#### log
>sudo journalctl -f -u home-assistant
