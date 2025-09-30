# v2ray-on-mikrotik

[فارسی](README.FA.md)

**install 3x-ui v2ray on mikrotik**

**How to use x-ray config on Mikrotik router  This was always a challenge until the very good feature of Mikrotik Docker Container solved this issue  In the video below you will see how we can easily and without any problems do this  complications**

# xray Config On Mikrotik Router

## 📺 Video Tutorial
🎥 Watch the full installation and usage guide on YouTube:  
👉 [Click here to watch the video](https://www.youtube.com/watch?v=131ONwrhPxg&t=72s)  

  
**Installation commands via MikroTik Docker container**

**Enter the following commands in order in the terminal**

**enable mikrotik container**

/system/device-mode/update container=yes  
/system/device-mode/print    

**Creating a virtual interface and giving it an IP address, and finally adding it to the Docker bridge and providing access to the internet**

/interface/bridge/add name=dockers  
/ip/address/add address=172.17.0.1/24 interface=dockers  
/interface/veth/add name=veth1 address=172.17.0.2/24 gateway=172.17.0.1  
/interface/bridge/port add bridge=dockers interface=veth1  
/ip/firewall/nat/add chain=srcnat action=masquerade src-address=172.17.0.0/24   

**If your server has IP version 6, you can configure it like this**

ipv6:fc07:55::1/64 set to bridge interface

ipv6:fc07:55::2/64 set to veth

**Configuring Docker Registry Link**  

container/config/set registry-url=https://registry-1.docker.io tmpdir=pull   

**Finally, add mounts and pull the Docker image**  
Mounts:  
src:/x-ui/db  
dst:/app/db  

Docker image : alireza7/x-ui:latest    

**Why we use this image for Docker**
**Ease of use, support for many protocols and most importantly, automatic restart after possible router reboot**

**If you have any problems, please refer to our YouTube video**  

https://www.youtube.com/@mikronet_plus  

#v2rayonmikrotik#v2rayclientonmikrotik  
V2ray Client on Mikrotik
