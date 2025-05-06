### Install Docker Engine on Raspberry Pi OS (64-bit)
#### Credit: https://dev.to/danshari/install-docker-engine-on-raspberry-pi-os-64-bit-8hl
This was tested on a Raspberry Pi 5 with a fresh install of Pi OS 64-bit bookworm.

These instructions are available on the official site, but they are somewhat hidden away.

If you want to skip reading the instructions I have made a script that you can run directly from the terminal of your Pi

```bash
sudo curl -sL https://raw.githubusercontent.com/ChutiponTri/Raspberry-pi-Docker/refs/heads/main/docker-pi.sh | bash
```

### Add GPG Keys
you will get no output from these commands

```bash
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Add the Docker repositories
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

this will also have no output

now update

```bash
sudo apt-get update
```

You should see a line with https://download.docker.com/linux/debian if the previous steps were completed correctly

### Install the Docker packages
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Test your installation
```bash
sudo docker run hello-world
```
