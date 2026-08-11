# How to set up Pi-hole inside of a Proxmox 9.2.10 LXC

Before getting started you will need to have Proxmox installed. If you don't already have it setup, I recommend this guide to get started https://www.youtube.com/watch?v=lFzWDJcRsqo&t
## Getting Setup
### Step 1.

Inside of the Proxmox Web UI select "local (pve)" --> "CT Templates" --> "Templates"
<img width="1775" height="773" alt="Screenshot From 2026-08-10 13-53-34" src="https://github.com/user-attachments/assets/2b0f515a-0913-44f5-a9e8-8e03c257e16d" />

### Step 2.

From the templates find "ubuntu-26.04-standard" click on it and click Download in the bottom right corner and wait for it to download.

<img width="1758" height="911" alt="Screenshot From 2026-08-10 13-54-48" src="https://github.com/user-attachments/assets/7818c6ef-3ac7-4599-9044-8ec8e0eef2c9" />


### Step 3.

In the Proxmox web UI click on "Create CT" in the top right corner.

<img width="1910" height="841" alt="Screenshot From 2026-08-10 13-55-50" src="https://github.com/user-attachments/assets/551f49a2-d9c0-42d3-9933-a6000166221e" />

### Step 4.

Select a "CT ID:" like 100, 101 or 102. If this is your first VM or container 100 is fine. Next click "Hostname:" and give it a name like "Pi-hole-ubuntu" after that create a password, then click Next. (A quick note on containers: they share the kernel with the host system, which is what makes them so lightweight. In a privileged container, root inside the container is also root on Proxmox. Leave the Unprivileged box checked, it's the default and all Pi-hole needs.)

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-56-57" src="https://github.com/user-attachments/assets/ab2ac987-0eea-4660-95bb-985e995816b7" />

### Step 5.

Now select "ubuntu-26.04-standard" from the "Template" drop down box, and click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-09" src="https://github.com/user-attachments/assets/d38c1820-0d70-4e0a-84e0-622b78cceef0" />

### Step 6.

The default 8GB of storage is enough for Pi-hole. Click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-26" src="https://github.com/user-attachments/assets/872b4c64-b0a4-47f8-ae94-0706445b8777" />

### Step 7.

The default 1 CPU core is enough. Click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-32" src="https://github.com/user-attachments/assets/ffe133cf-bfd0-437f-913f-6da06a573345" />

### Step 8.

The default 512MB of RAM is enough. Click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-38" src="https://github.com/user-attachments/assets/25d024ba-7600-4d25-a125-dedecec67c85" />

### Step 9.

Now this is where you would enter your static IP address, but for this guide select DHCP to get an IP address from your router, then click Next.

<img width="1233" height="817" alt="Screenshot From 2026-08-10 13-58-56" src="https://github.com/user-attachments/assets/69f34df7-a73e-41cb-8243-89eeb8e0dc64" />

### Step 10.

Leave the DNS settings at default, and click next.

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

### Step 14.

Now copy and paste this command and hit the enter key to update Ubuntu before installing Pi-hole. (Note: ``-y`` automatically answers yes to the confirmation prompts, so you don't have to sit there hitting Y.)
```
apt update && apt upgrade -y
```
<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-04-37" src="https://github.com/user-attachments/assets/220cfb81-8c6b-42da-93e0-8d4cab3a56c8" />

### Step 15.

Now you need to install Curl. Copy and paste the command below and hit the enter key.
```
apt install -y curl
```

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-08-01" src="https://github.com/user-attachments/assets/cf69e651-71e6-4668-8b14-c0e051e3b596" />

### Step 16.

Time to install Pi-hole from the official GitHub account by copy and pasting the command below and hitting the enter key. Or if you would prefer here's a link to Pi-hole GitHub where you can verify the command: https://github.com/pi-hole/pi-hole/#one-step-automated-install
```
curl -sSL https://install.pi-hole.net | bash
```
<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-08-48" src="https://github.com/user-attachments/assets/ad9575b4-3fb7-4305-a7b0-b01ff66b257f" />
You should see this screen.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-08-57" src="https://github.com/user-attachments/assets/4059e030-cc1a-4d83-9f3b-a73c58457037" />

## Configuring Pi-hole
### Step 17.

Hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-08" src="https://github.com/user-attachments/assets/40b357eb-33ed-4c90-a217-24922dc31a25" />

Again you hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-24" src="https://github.com/user-attachments/assets/050efef8-d9d8-4b4e-9266-1093503f0f90" />

This screen is just to remind you that having a static IP address is important by either setting one manually or setting a DHCP reservation. Select "Continue" and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-46" src="https://github.com/user-attachments/assets/5ef1dc47-d5fc-4604-9a0c-e1a1f9914d01" />

Next select your preferred DNS provider. Google DNS is the default and the one used in this guide, but select the one you want and select "OK" and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-10-52" src="https://github.com/user-attachments/assets/4bf76f92-b066-4b5e-9a60-5ca86b2c3eae" />

StevenBlack's block list is the Pi-hole default and the recommended one to start out with.
Select "Yes" and hit the enter key.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-11-06" src="https://github.com/user-attachments/assets/e9b3759a-10a2-48a1-b14d-014928997740" />

Most people will want to enable query logging. Select "Yes" and hit enter.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-11-42" src="https://github.com/user-attachments/assets/491a628b-cfe5-4a9c-a825-f7104fcfee48" />

Same as above. Select "Show everything" then "Continue" and hit enter.

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-11-49" src="https://github.com/user-attachments/assets/9195de71-9214-42d1-b6fd-4fe278109e84" />

Now the installation is complete and it will show you a screen with the IP address of the Admin webpage and Admin password. (Note: your IP address and password will be different than what's shown)

<img width="1917" height="815" alt="Screenshot From 2026-08-10 14-13-07" src="https://github.com/user-attachments/assets/b444bdaf-a26e-4fa0-b7b0-598e78515f06" />

### Step 18.

To access the web interface you will need to open your favorite web browser and type in the Pi-hole IP address in the URL bar at the top. (Note: Clicking on any option that says "search the web" will search the web for your IP address and not take you to your local Pi-hole IP address)

<img width="1078" height="123" alt="Screenshot From 2026-08-10 14-17-11" src="https://github.com/user-attachments/assets/150b56dc-031f-4ab0-b436-6bcc7e469eb1" />

### Step 19.

Now you should be on the Pi-hole login page and where it says "Consider upgrading to HTTPS"
click on "HTTPS". 

<img width="830" height="856" alt="Screenshot From 2026-08-10 14-20-08" src="https://github.com/user-attachments/assets/2295d9c0-f52b-4441-bd5f-79f80a3eafe8" />

You will now get a warning from your browser about the site you are about to visit, but you are the one who set the site up so it's safe to continue and click on advanced. (Note: These warnings are due to Pi-hole using a self signed certificate that your web browser can't verify. This is safe to ignore here but is not something you should do outside of your home network.)

<img width="1095" height="595" alt="Screenshot From 2026-08-10 14-20-28" src="https://github.com/user-attachments/assets/928de29c-9c06-404d-a961-fd185999295f" />

It's safe to ignore this warning also and click on the IP address at the bottom to continue. 

<img width="1152" height="967" alt="Screenshot From 2026-08-10 14-20-44" src="https://github.com/user-attachments/assets/91df5f69-a825-4e7f-9fa8-29067dbd3684" />

Now you should be back at the Pi-hole login but this time you're connected to it through HTTPS which is encrypted via TLS.

<img width="1152" height="967" alt="Screenshot From 2026-08-10 14-21-02" src="https://github.com/user-attachments/assets/dc7b75b9-cf9e-4fc5-b3a2-91a590850e7c" />

## Logging In
### Step 20.
Now enter the password Pi-hole generated for you at the end of installation and click "Login"

<img width="1152" height="967" alt="Screenshot From 2026-08-10 14-21-54" src="https://github.com/user-attachments/assets/436b8c4a-0e3a-4414-b1a0-2817e9420811" />

You will now see the Pi-hole dashboard.

<img width="1573" height="1003" alt="Screenshot From 2026-08-10 14-23-32" src="https://github.com/user-attachments/assets/aec2e14a-73e8-4f0f-8ba4-c73f65202010" />

### Step 21.
Time to test that it works. From another machine enter the command below with your Pi-hole IP address and it should come back 0.0.0.0, and the dashboard query counter should tick up. (Note: The 192.168.1.16 IP address is for example purposes and you need to enter your Pi-hole IP address) (Also make sure to replace the "< >" with your Pi-hole IP)
```
nslookup doubleclick.net <pihole-ip> 
```
<img width="922" height="565" alt="Screenshot From 2026-08-11 12-54-49" src="https://github.com/user-attachments/assets/1aa92d62-e483-47b0-8aed-35221d4abbe8" />

This is what the command should output.

<img width="922" height="565" alt="Screenshot From 2026-08-11 12-54-57" src="https://github.com/user-attachments/assets/a9292204-c68d-49ce-b20e-9fad966818bc" />

And if your dashboard updates showing it has blocked ad traffic, it's working.

<img width="1555" height="630" alt="Screenshot From 2026-08-11 12-55-17" src="https://github.com/user-attachments/assets/1cb89efb-0da4-44e3-90ee-280e62d92793" />


## Final Steps
### Step 22.

After everything is setup you should log into your router and set a DHCP reservation, if you are not sure how to, Google "Router model + how to set DHCP reservation" or you can ask your favorite AI model.
Here's an example of what mine looked like.

<img width="480" height="968" alt="Screenshot From 2026-08-10 14-15-13" src="https://github.com/user-attachments/assets/06430bfc-7300-47fe-b150-aec32ffd3a4a" />

### Step 23.

It's time to make a new password to replace the randomly generated one. 
Go back to Proxmox and click on the console and copy paste this command and hit enter.
```
pihole setpassword
```

<img width="1157" height="331" alt="Screenshot From 2026-08-10 19-53-39" src="https://github.com/user-attachments/assets/d53bb183-16a5-4566-bce7-552f3f91e6ae" />

Now it will ask you to enter your new password and to retype it.

<img width="1157" height="331" alt="Screenshot From 2026-08-10 19-54-39" src="https://github.com/user-attachments/assets/38136888-47f5-4ef0-b1ff-799aa04a0d3b" />

### Step 24.

This is more of a maintenance step for the future, because Pi-hole was just installed it is already up to date. Enter this command into the the console to update Pi-hole. 
```
pihole -up
```

<img width="1157" height="331" alt="Screenshot From 2026-08-10 20-53-31" src="https://github.com/user-attachments/assets/e3e6e2c6-24a0-4de7-b65d-251bf100dae9" />

### Step 25.

There's one last warning to clean up. Due to how pihole-FTL tries to sync the clock via NTP, and an unprivileged container isn't allowed to set the system clock. It inherits the host's.

<img width="1573" height="1003" alt="Screenshot From 2026-08-10 14-23-45" src="https://github.com/user-attachments/assets/a791cf46-06e8-482d-b95a-4090cac9e81e" />

Here's the command to fix that warning.
```
pihole-FTL --config ntp.sync.active false
```

<img width="1401" height="792" alt="Screenshot From 2026-08-10 14-25-38" src="https://github.com/user-attachments/assets/568e986a-c4bb-4d13-bb16-fabc04272a69" />


Now you should be all set, and from here you can set your router's LAN DNS provider to the Pi-hole's IP address or set it for individual devices. Here's an example of what the Unifi Cloud Gateway setting looks like. (Note: some ISP-supplied routers won't let you change it at all. So you will need to set DNS per-device. Or Pi-hole has an option to operate as DHCP server which is outside of the scope for this guide.)

<img width="466" height="326" alt="Screenshot From 2026-08-11 13-30-03" src="https://github.com/user-attachments/assets/14bdf80d-06e4-44f2-bf6a-c622dca1d8ef" />

Devices keep their old DNS until their lease renews. Reboot them or wait.


From here you can adjust if you need to give Pi-hole more resources like CPU cores or RAM. You can also look into adding more block lists, look into things like Unbound DNS for self hosted DNS resolution, adding more Pi-hole instances for redundancy, or Syncing them using things like Nebula Sync or Gravity-Sync.

Thanks for reading.

