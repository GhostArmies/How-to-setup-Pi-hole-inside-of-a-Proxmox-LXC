# How-to-setup-Pi-hole-inside-of-a-Proxmox-LXC

Before getting started you will need to have Proxmox installed. If you don't already have it setup, I recommend this guide to get started https://www.youtube.com/watch?v=lFzWDJcRsqo&t
## Getting Setup
### Step 1.

Inside of the Proxmox Web UI select "local (pve)" --> "CT Templates" --> "Templates"
<img width="1775" height="773" alt="Screenshot From 2026-08-10 13-53-34" src="https://github.com/user-attachments/assets/2b0f515a-0913-44f5-a9e8-8e03c257e16d" />

### Step 2.

From the templates find "ubuntu-26.04-standard" click on it and click Download in the bottom right corner and wait for it to download.

<img width="1758" height="911" alt="Screenshot From 2026-08-10 13-54-48" src="https://github.com/user-attachments/assets/7818c6ef-3ac7-4599-9044-8ec8e0eef2c9" />


### Step 3.

In the Proxmox web UI click on "Create CT" in the to right corner.

<img width="1910" height="841" alt="Screenshot From 2026-08-10 13-55-50" src="https://github.com/user-attachments/assets/551f49a2-d9c0-42d3-9933-a6000166221e" />

### Step 4.

Select a "CT ID:" like 100, 101 or 102. If this is your first VM 100 is fine. Next click "Hostname:" and give it a name like "Pie-hole-ubuntu" after that create a password then click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-56-57" src="https://github.com/user-attachments/assets/ab2ac987-0eea-4660-95bb-985e995816b7" />

### Step 5.

Now select "ubuntu-26.04-standard" from the "Template" drop down box and click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-09" src="https://github.com/user-attachments/assets/d38c1820-0d70-4e0a-84e0-622b78cceef0" />

### Step6.

The default 8GB of storage is enough for Pi-hole. Click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-26" src="https://github.com/user-attachments/assets/872b4c64-b0a4-47f8-ae94-0706445b8777" />

### Step 7.

The default 1 CPU core is enough. Click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-32" src="https://github.com/user-attachments/assets/ffe133cf-bfd0-437f-913f-6da06a573345" />

### Step 8.

The default 512MB of RAM is enough. Click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-38" src="https://github.com/user-attachments/assets/25d024ba-7600-4d25-a125-dedecec67c85" />

### Step 9.

Now this is where you would enter your static IP address. But for this guide select DHCP to get an IP address from your router, then click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-56" src="https://github.com/user-attachments/assets/69f34df7-a73e-41cb-8243-89eeb8e0dc64" />

### Step 10.

Leave the DNS settings at default and click next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-59-04" src="https://github.com/user-attachments/assets/cdd3e4fc-87f6-4190-ad34-9cafb7c9d95b" />

### Step 11.

Now review the settings and click Finish.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-59-13" src="https://github.com/user-attachments/assets/7ff79ed1-f832-4f1e-998d-caa3cc7a45cf" />

## Installing Pi-hole
### Step 12.

Next select the newly created container, and then click "Start" in the top right.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-00-03" src="https://github.com/user-attachments/assets/aefc2d98-de4f-4326-b9da-72d129171af3" />

### Step 13.

Click on "Console" and enter the default login which is "root" and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-00-58" src="https://github.com/user-attachments/assets/a349e7bb-441c-4ccb-bc30-2fb585fd302e" />
Next enter the password you made during setup and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-01-08" src="https://github.com/user-attachments/assets/92b666a9-b27f-44df-a7ab-8d2fba29411c" />
You should now be signed in and see this screen.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-01-14" src="https://github.com/user-attachments/assets/ffe42b06-a62b-4940-95f5-0908b924cb0b" />

### Step 13.

Now copy and paste this command and hit the enter key to update Ubuntu before installing Pi-hole.
```
sudo apt update && sudo apt upgrade
```
<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-04-37" src="https://github.com/user-attachments/assets/220cfb81-8c6b-42da-93e0-8d4cab3a56c8" />

### Step 14.

Now you need to install Curl. Copy and paste the command below and hit the enter key.
```
apt get curl
```

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-08-01" src="https://github.com/user-attachments/assets/cf69e651-71e6-4668-8b14-c0e051e3b596" />

### Step 15.

Time to install Pi-hole from the official Github account by copy and pasting the command below and hitting the enter key.
```
curl -sSL https://install.pi-hole.net | bash
```
<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-08-48" src="https://github.com/user-attachments/assets/ad9575b4-3fb7-4305-a7b0-b01ff66b257f" />
You should see this screen.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-08-57" src="https://github.com/user-attachments/assets/4059e030-cc1a-4d83-9f3b-a73c58457037" />

## Configuring Pi-hole
### Step 16.

Hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-08" src="https://github.com/user-attachments/assets/40b357eb-33ed-4c90-a217-24922dc31a25" />

Again you hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-24" src="https://github.com/user-attachments/assets/050efef8-d9d8-4b4e-9266-1093503f0f90" />

This screen is just to remind you that having a static IP address is important by either setting one manually or setting a DHCP reservation. Select "Continue" and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-46" src="https://github.com/user-attachments/assets/5ef1dc47-d5fc-4604-9a0c-e1a1f9914d01" />

Next select your preferred DNS provider. Google DNS is the default and the used in this guide, but select the one you want and select "OK" and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-52" src="https://github.com/user-attachments/assets/4bf76f92-b066-4b5e-9a60-5ca86b2c3eae" />

StevenBlack's block list is the Pi-hole default and the recommended one to start out with.
Select "Yes" and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-11-06" src="https://github.com/user-attachments/assets/e9b3759a-10a2-48a1-b14d-014928997740" />

Most people will want to enable query logging. Select "Yes" and hit enter.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-11-42" src="https://github.com/user-attachments/assets/491a628b-cfe5-4a9c-a825-f7104fcfee48" />

Same as above. Select "Show everything" then "Continue" and hit enter.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-11-49" src="https://github.com/user-attachments/assets/9195de71-9214-42d1-b6fd-4fe278109e84" />

Now the installation is complete and it will show you a screen with the IP address on the Admin webpage and and Admin password. (Note: your IP address and password will be different that what's shown)

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-13-07" src="https://github.com/user-attachments/assets/b444bdaf-a26e-4fa0-b7b0-598e78515f06" />

### Step 17.

To access the web interface you will need to open your favorite web browser and type in the Pi-hole IP address in the URL bar at the top.

<img width="1078" height="123" alt="Screenshot From 2026-08-10 14-17-11" src="https://github.com/user-attachments/assets/150b56dc-031f-4ab0-b436-6bcc7e469eb1" />


