# v2ray-on-mikrotik

**install 3x-ui v2ray on mikrotik**

How to use x-ray config on Mikrotik router  This was always a challenge until the very good feature of Mikrotik Docker Container solved this issue  In the video below you will see how we can easily and without any problems do this without any complications

# xray Config On Mikrotik Router

youtube video  
[آموزش استفاده از V2Ray در روترهای میکروتیک - YouTube](https://www.youtube.com/watch?v=131ONwrhPxg)
**Installation commands via MikroTik Docker container**

**enable mikrotik container**

/system/device-mode/update container=yes  
/system/device-mode/print    

**Creating a virtual interface and giving it an IP address, and finally adding it to the Docker bridge and providing access to the internet**

/interface/bridge/add name=dockers  
/ip/address/add address=172.17.0.1/24 interface=dockers  
/interface/veth/add name=veth1 address=172.17.0.2/24 gateway=172.17.0.1  
/interface/bridge/port add bridge=dockers interface=veth1  
/ip/firewall/nat/add chain=srcnat action=masquerade src-address=172.17.0.0/24    

**Configuring Docker Registry Link**  

container config: https://registry-1.docker.io  

**Finally, add mounts and pull the Docker image**
Mounts:  
src:/x-ui/db  
dst:/app/db  

Docker image : alireza7/x-ui:latest    

**Why we use this image for Docker**
**Ease of use, support for many protocols and most importantly, automatic restart after possible router reboot**

**If you have any problems, please refer to our YouTube video**
#v2rayonmikrotik
