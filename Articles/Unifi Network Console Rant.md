https://www.reddit.com/r/UNIFI/comments/1ajk1k5/unifi_network_console_rant/

I understand that this is mostly a rant from a single home user and not from a company or anything like that. I'm just frustrated that this Ubiquiti tries to be this great software company but so many of their problems have been here for a long time based on some of my research. 

# Complaints

## DHCP Server
I see frequently. I get an alert that more than one device isusing the same IP address on my IOT network.  None of them have screens so I can't actual tell if they are really getting the .125 address or not but I don't set anything manual here. 
![[Pasted image 20240205085643.png]]

## Connected Devices and Topology Map
After several reboots and days with no changes, the Device to Port map is never right.  Also the Experience or connection speed is wrong. In this image below you'll see that US8_B says E, even though it's very much green for Gigabit on the switch and I can get data to move at full gigabit no problem. 
![[Pasted image 20240205085916.png]]

In the image below you'll see  the three 100 megabit devices connected to the UMD Pro actually think they're connected to US8_B. It's a Ras Pi - Hue Bridge - Printer. 
![[Pasted image 20240205090158.png]]

DietPi, Printer, Hue bridge all show as Gigabit but are only Fast Ethernet and show connected to the US8_B switch, that's also just not correct at all, they're all connected to UDM Pro as seen above. 
![[Pasted image 20240205090730.png]]

Meaning my Topology is just wrong. Like I can kind of accept this but if i was a business this would be unacceptable. 
![[Pasted image 20240205090950.png]]