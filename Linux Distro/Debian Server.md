---
tags:
  - network
  - debian
  - staticip
  - nano
  - server
  - linux
  - homelab
---
Edit your networking settings
```
sudo nano /etc/network/interfaces
```

*Config Example - Check your Interface name - VM vs Bare Metal will have different names.
***

> [!warning]
>The Auto ENS18 is important! 

>[!tip]
>NOTE - Sometimes if the spaces don't work  - delete the spaces and add tabs

***
```bash
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug ens18
auto ens18
iface ens18 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	gateway 192.168.1.1
	dns-nameservers 192.168.1.2 192.168.1.3
	dns-domain post.home

# This is an autoconfigured IPv6 interface
#iface ens18 inet6 auto
```


###### Notes
[[Debian Server|Debian]]  is the core upstream for [[Ubuntu]] 



# How to Create a SUDO User Debian

IT admins often require access to privileged areas of a system in order to make changes, updates, and patches. Implementing these changes via a root user account is risky, because super users have the ability to change every aspect of a system. One mistake could have disastrous consequences or run afoul of security and compliance. 

Sudo user accounts offer privileged access to necessary parts of your system, without allowing the user to tamper with any sensitive or critical information. Creating these accounts has numerous benefits: 

- **Permission management:** By adding users to the sudo group, you can control which users have the ability to execute specific tasks requiring administrative privileges, allowing better management of system security.

- **Temporary privilege elevation:** Users can use the sudo command to temporarily run specific commands or tasks with elevated administrator privileges without having to maintain a constant administrative login.

- **Logging and auditing:** The system logs each use of the sudo command, tracking which users performed what operations. This helps trace and audit system activities.

- **Granular control:** By appropriately configuring the sudoers file, different users can be assigned different sudo privileges, allowing fine-grained control over system resources and functionality.  
    

Note that it is important to manage sudo group members and their associated permissions carefully. Only trusted users should be added to the sudo group, and their privileges should be managed diligently to ensure system security.

## How to add a root user to a sudo group

If you’re beginning with a root user account and would like to create a sudo user out of it, follow these steps to reduce privileges and secure access. 

### 1. Create a new user

Create a new user using the following command:

**adduser [username]**

Replace **[username]** with your desired username. Follow the prompts to enter the necessary user information and password. Note: It is highly recommended that you set a strong, complex password for all sudo accounts. 

![screenshot of code](https://jumpcloud.com//wp-content/uploads/2023/09/1.png)

### 2. Add user to the sudo group

Add the user to the sudo group using the following command:

**usermod -aG sudo [username]** 

This will add the user to the “sudo” group.

![screenshot of code](https://jumpcloud.com//wp-content/uploads/2023/09/2.png)

### 3. Verify sudo privileges

To confirm the successful addition, you can try running the following command to check if the new user has sudo privileges:

**sudo -l -U [username]**

Replace **[username]** with the actual username you added. If it displays the user’s sudo privileges, then the addition was successful.

### 4. Switch to user and test whether sudo works

Switch user command:

**su [username]**

Replace **[username]** with the actual username you added. After the user is switched, run the sudo command for verification:

**sudo apt update**

## How to add a normal (non-root) user to a sudo group 

If the current user is not root, use these steps to convert a basic user account into a sudo user. 

### 1. Create a new user

Create a new user using the following command:  

**sudo adduser [username]**

Replace **[username]** with the desired username. Follow the prompts to enter the necessary user information and password. Note: It is strongly recommended to set a strong password for the new user.

![screenshot of code](https://jumpcloud.com//wp-content/uploads/2023/09/3.png)

### 2. Add user to the sudo group

Add the user to the sudo group using the following command:

**sudo usermod -aG sudo [username]**

This will add the user to the “sudo” group.

![screenshot of code](https://jumpcloud.com//wp-content/uploads/2023/09/4.png)

### 3. Verify sudo privileges

To confirm the successful addition, you can try running the following command to check if the new user has sudo privileges:

**sudo -l -U [username]**

Replace **[username]** with the actual username you added. If it displays the user’s sudo privileges, then the addition was successful.

### 4. Switch to user and test whether sudo works

Switch user command:

**sudo su [username]**

Replace **[username]** with the actual username you added. After the user is switched, run the sudo command for verification:

**sudo apt update**

## Secure all Linux distros with sudo users 

In this tutorial, we demonstrated how to create a sudo user on Debian. These basic steps can be applied to other Linux distributions, and it’s always recommended you create sudo users instead of using root user accounts. Want to see the steps for creating sudo users in other Linux distros? Check out the tutorials below.