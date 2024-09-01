# Install

## Server
Download script install Wazuh, + ex config indexer
```
curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh
curl -sO https://packages.wazuh.com/4.8/config.yml
# configure the config.yml
```
Install
```
bash wazuh-install.sh --generate-config-files
```
Indexer installation 
```
bash wazuh-install.sh --wazuh-indexer machinename
```
Launch indexer cluster
```
bash wazuh-install.sh --start-cluster
```
Configure password
```
tar -axf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt -O | grep -P "\'admin\'" -A 1
```
Install server
```
bash wazuh-install.sh --wazuh-server machinename
```
Install dashboard
```
bash wazuh-install.sh --wazuh-dashboard machinename
```

## Agent
Install repository
```
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import && chmod 644 /usr/share/keyrings/wazuh.gpg
echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list
apt-get update
```
Env variable for wazuh server's ip address
```
WAZUH_MANAGER="192.168.1.10" apt-get install wazuh-agent
#ip server wazuh
systemctl daemon-reload
systemctl enable wazuh-agent
systemctl start wazuh-agent
```
```
```
