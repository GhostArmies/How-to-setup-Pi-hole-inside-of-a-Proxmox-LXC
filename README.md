# How-to-setup-Pi-hole-inside-of-a-Proxmox-LXC

Before getting started you will need to have Proxmox installed. If you don't already have it setup, I recommend this guide to get started https://www.youtube.com/watch?v=lFzWDJcRsqo&t

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

