<b>Install Sycnthing on Ubuntu 22.04</b></br>
</br>
Update system</br>
</br>
```
apt update && apt upgrade -y
```
</br>
Install syncthing</br>
</br>
```
apt install syncthing -y
```
</br>
use nano to create systemd file</br>
</br>
```
nano /etc/systemd/system/syncthing@.service
```
</br>
Copy and paste the following inside the systemd file</br>
</br>
```
[Unit]
Description=Syncthing - Open Source Continuous File Synchronization for %I
Documentation=man:syncthing(1)
After=network.target

[Service]
User=%i
ExecStart=/usr/bin/syncthing -no-browser -gui-address="0.0.0.0:8384" -no-restart -logflags=0
Restart=on-failure
SuccessExitStatus=3 4
RestartForceExitStatus=3 4

[Install]
WantedBy=multi-user.target
```
</br>
Reload the systemd configuration</br>
</br>
```
systemctl daemon-reload
```
</br>
Start syncthing service</br>
</br>
```
systemctl start syncthing@root
systemctl status syncthing@root
```
</br>
Enable the service to start on boot</br>
</br>
```
systemctl enable syncthing@root
```

Done! (Don't forget to setup a password on the webui!!
