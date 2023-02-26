<center>

# **PL3 Setup**

## **1. Connect the wifi adapters:**
</center>

- Go to the settings page of your VM</br><center>
![image](images/image.png "settings")</br></br>

- Go to the network section and copy the following setup:</br><center>
![image2](images/image3.png "setup adapter 1")</br>
![image3](images/image4.png "setup adapter 2")</br></br>

- Afterwards, turn on your VM and connect both adapters:</br><center>
![image4](images/image5.png "connect adapters")</br></br>
---

- ## ***Both previous configurations and the Client configurations are needed on the the VPN and Server VMs. Do the following steps on the VM which will run as the client and then clone the VM***

---
<center> 

## **2. Client**

</center> 

- **1. Install openvpn:**
``` bash
yum install openvpn
```
- **2. Go to this folder:**
```bash
cd /usr/share/doc/openvpn-2.4.12/
```
- **3. Go to this folder:**
``` bash
cd sample/sample-config-files/
```
- **4. And copy the server.conf file to another location (don't change the original)**
``` bash
cp server.conf {folder}
```
- **5. Change the permissions of the file in case you can't edit it (you may not need this step)**
``` bash
sudo chmod o+rwx {path/roadwarrior-client.conf}
```
- **6. Copy the next file to the openvpn folder:**
``` bash
cp distro/rpm/openvpn.init.d.rhel /etc/rc.d/init.d/openvpn
```
- **7. Copy the roadwarrior-client.conf to the same location where you saved the server.conf file**
``` bash
cp roadwarrior-client.conf {path}
```
- **8. Change the permissions of the file in case you can't edit it (you may not need this step)**
``` bash
sudo chmod o+rwx {path/roadwarrior-client.conf}
```
- **9. Check if everything is in order with ifconfig** (The first two entries show what you are looking for - enp0s3 and enp0s8)**:**
``` bash
ifconfig
```

- **10. Install Apache server** (thecnically only needed on the VPN VM, but it's fine to have it on all of them)**:**
``` bash
yum install httpd
```
- **Note:** to run the apache server, afterwards, run the following command:
``` bash
systemctl start httpd
```
---
<center>

## **3. Clone the VM**

</center>

- **1. Press right click on top of your VM and select clone (Ctrl + O).**
- **2. Change the name accordingly to if it is the VPN or the Server VM. (not mandatory but it helps to keep track of the VMs)**
- **3. change the MAC Address Policy to "Generate new MAC address for all network cards" and press next.**</br></br>
![image](images/image6.png "clone")
- 4. Press "Full clone" and press finish.

--- 

## **4. Setup the connections**
- **Follow the next steps to configure your network:**
1. Click on wired settings;

![image](images/image7.png "wired settings")
2. Click on the enp0s8 settings; 
![image](images/image8.png "click on the enp0s8 settings")
3. Setup the addresses and networks for all your VMs. 
![image](images/image9.png "enps0s8 settings")

- ***Tip - use the following image to help you setup your network:***
![image](images/image10.jpg "network setup")

---
