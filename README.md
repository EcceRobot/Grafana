# Grafana

## Set up a server running Grafana

Let's use repository instead od downloading the .deb packege.
In this way you can update Grafana in an easy way.

Create a file _/etc/apt/sources.list.d/grafana.list_ and add the following to it.
```
deb https://packages.grafana.com/oss/deb stable main
```
This allows you to install signed packages.
```
curl https://packages.grafana.com/gpg.key | sudo apt-key add -
```
You may need to install the apt-transport-https package which is needed to fetch packages over HTTPS.
```
sudo apt-get install -y apt-transport-https
```
Update your Apt repositories and install Grafana
```
sudo apt-get update
sudo apt-get install grafana
```
Start the server (via systemd)
```
systemctl daemon-reload
systemctl start grafana-server
systemctl status grafana-server
```
### Enable the systemd service so that Grafana starts at boot.
```
sudo systemctl enable grafana-server.service
```

### Logging in for the first time

To run Grafana open your browser and go to http://localhost:3000/.

Default username is _admin_ and default password is _admin_. When you log in for the first time you will be asked to change your password.
