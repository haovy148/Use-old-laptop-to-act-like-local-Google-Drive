# Use-old-laptop-to-act-like-local-Google-Drive


Hello guys, everyone uses Google Drive with 15gb budget, I luckily have Gemini Pro with its benefits, but It going to expired soon this Oct. So, I want to
+Build my self a Google Drive home Server!
+Take advantage of my old laptop.
+Can be used for future project like a server for my Apps!

## SPECS
I had to open my laptop to change the componpents. My laptop is DELL 3565 AMD A6 9200 with 2 x 4GB Ram and 500GB HDD.
<img width="1160" height="728" alt="image" src="https://github.com/user-attachments/assets/438e2807-3b42-461f-89be-e3e6ffe147f6" />

<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/22d2f509-27ad-46cf-ac85-052c19609d4c" />
This laptop barely could do anything within Window nor Ubuntu GONME. It is reborn with Lubuntu, also a Ubuntu distro, but for super weak ones.


I chooose Lubuntu for the GUI, because I could not do anything with Ubuntu Server, this one merely works on Terminal.

HDD works just fine on Linux, it is cheap, reliable, and large storage will do its job.

Also, This Chip is crazily weak, 2 cores and only reach no more than 2.5 GHZ. But for the server, It will be fine.

Note: I have to use this 2.5 kg of plastic though out my high school years, and until College I started to know Linux. So slow processing isn't a pain in my ass.
 <img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/1a4d0c52-d97a-4dad-92cf-c234650a7ef2" />


## Set UP

So our build here is : Docker -> Seafile -> And TailScale.
TailScale is a website allows us to reach our website from anywhere. It is basically a free IP. This one easier to resgiter duck.org or netcloud, and it is free!

Seafile will be hosted from our laptop

And Docker is a tool to control the Seafile. It contains containers include Seafile, which has many parts: like the database, web GUI, and server.

So docker just like a script that helps to run all of them at a same time without manually activite them.

so to do this, just

```py
sudo apt update
sudo apt install ca-certificates curl

sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
docker compose version

sudo mkdir -p /opt/seafile
cd /opt/seafile


```
Now, your main focus is edit .env

you shall see something like this

```py
SEAFILE_SERVER_HOSTNAME=   // for this one, you need to use tailscale and sign up for a IP domain, then copy that domain to here!
SEAFILE_SERVER_PROTOCOL=https
TIME_ZONE=
CACHE_PROVIDER=redis

INIT_SEAFILE_ADMIN_EMAIL=
INIT_SEAFILE_ADMIN_PASSWORD=
JWT_PRIVATE_KEY=

// put your detail to that txt file. Read carefully
// Ctrl + O -> Enter -> Ctrl + X exit 
```
## Use any browser to signup for Tailscale. 

Sign up for the first, and second devices. Then, obtain your main IP for hosting the server. Now, your laptops can communicate though Tailscale.


## useful start up

```py
sudo docker compose down && sudo docker compose up -d
```

This server is extremely light, using around 2GB ram, and light on CPU usage

<img width="1347" height="750" alt="image" src="https://github.com/user-attachments/assets/d805ba94-9c33-46f6-808e-2d92517f0b1f" />

And the uploading time is fast too!

<img width="1771" height="848" alt="image" src="https://github.com/user-attachments/assets/b4844712-d3a6-4fe6-b416-cbc581446eb4" />


