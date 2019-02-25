# Docker Configuration

## Setup log rotate on host
```bash
sudo bash -c "cat >> /etc/docker/daemon.json" << EOL
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  }
}
EOL

sudo systemctl restart docker
```


