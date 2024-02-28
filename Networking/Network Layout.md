

# Outdated data as of 2/1/2024


**Networking Layout - Updated 12/15/2023**
I’ve put much effort into my network layout and here is an attempt at physical layout based on what I have.

**Physical Layout of the House Port Box in the Utility Room**

| Column 1 | Column 2 | Column 3 |
| ---- | ---- | ---- |
| 1. Master Bedroom > Apple TV | 2. Living Room > Apple TV | 3. Office > US-8 Switch |
| 4. Empty | 5. Everett Bedroom > AC-Lite | 6. Living Room > AC-Pro |
# House Port 
1. Master Bedroom > [[Apple TV]]
2. Living Room > Apple TV
3. Office > US-8 Switch
4. Empty
5. Everett Bedroom > Disconnected
6. Living Room > AC-Pro

# Top Keystone Panel
| **Keystone Slot #** | **9** | **10** | **11** | **12** | **13** | **14** | **15** | **16** |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **Switch Name** | - | - | - | [[UMD-Pro]] | [[UMD-Pro]] | [[UMD-Pro]] | [[UMD-Pro]] | [[UMD-Pro]] |
| **Switch Port #** | - | - | - | 1 | 3 | 5 | 7 | SFP10 |
| **House Port #** | - | - | - | - | - | - | 6 | 3 |
| **Destination Device** | - | - | - | Proxmox 2.5G | Proxmox 1.0G | - | AC Pro | US-8 Office |
# Bottom Keystone Panel
| **Keystone Slot #**    | **9** | **10**  | **11**  | **12**   | **13**   | **14**  | **15**       | **16**       |
| ---------------------- | ----- | ------- | ------- | -------- | -------- | ------- | ------------ | ------------ |
| **Switch Name**        | -     | [[UMD-Pro]] | [[UMD-Pro]] | [[UMD-Pro]]  | [[UMD-Pro]]  | -| -            | [[UMD-Pro]]      |
| **Switch Port #**      | -     | 2       | 4       | 6        | 8        | -       | -            | 9            |
| **House Port #**       | -     | -       | -       | 1        | 2        | -       | -            | -            |
| **Destination Device** | -     | DietPi  | Printer | Apple TV | Apple TV | -       | Modem Port 2 | Modem Port 1 |
# Other Devices 
| **NOTE**               | **Not in a Keystone**      |
| ------------------ | ---------------------- |
| **Switch Name**        | US-8 -Office           |
| **Switch Port #**      | 8                      |
| **House Port #**       | -                      |
| **Destination Device** | POE Injector > AC Lite |
# Cable Map (Left to Right on Wall)
1. External not terminated - White - (Far Left)
2. Everett bedroom - White - (POE Required)
3. Master bedroom - White 
4. Dead cable  to the TV area buried -Blue Folded up
5. Office Bedroom - to Switch - blue
6. TV 1 - Goes to Device  
7. TV 2 - Goes to AP (POE Required)
  
[Google Doc With layout](https://docs.google.com/spreadsheets/d/1ycKH25E38s2Hnmlmwt-8QHcLR6CIY3Dt8aBdPO1WDYU/edit#gid=1988531776)
