# CQU-Y25T2-COIT13236-G06-DST-UG25T2 (Bridging the Digital Divide)
This repository's purpose is for a portfolio relating to the project reflection task in the COIT13236 (2025 T2).

Actual group can be found [here](https://github.com/cquict2025/nis-y25t2-project-g06-dst-ug25t2)

# Portfolio
My main technical artefact for this project with my largest contributions is the Security Testing document of our project solution.

* Main GitHub Repository [Copy](https://github.com/cquict2025/nis-y25t2-project-g06-dst-ug25t2/blob/main/documents/performance%20and%20testing/12161580%20-%20Security%20Testing%20-%20G06-DST-UG25T2.docx)
* Word Document via SharePoint [Copy](https://cqu365.sharepoint.com/:w:/r/sites/coit13236cybersecurityprojectht22025-G06-MEL-UG25T1/Shared%20Documents/G06-DST-UG25T2/Deliverables/12161580%20-%20Security%20Testing%20-%20G06-DST-UG25T2.docx?d=wb763c650d6684a9a8d9550e156d6c167&csf=1&web=1&e=ulY9WK)

This document contains the necessary information that outlines the setup, hardware used, and all the testing processes involved to evaluating the security of the platform, as well as identifying any risks and then providing mitigations for any said risks.

## Showcasing Crucial Security Testing Results 
This section will briefly show a section of the main document to showcase a crucial recommendation to our digital solution.

In Kali Linux, once the onboard Wi-Fi interface is switched into monitor mode to allow wireless testing, we can use the tool called *airodump* to lock in a specific channel which was gained from an initial reconnaisance scan. This test involved mounting a de-authentication attack on a client within the network to forcibly disconnect them. This test checks for a feature within Access Points known as *802.11w (Protected Management Frames)*. If present, this will prevent the de-authentication attack, otherwise it will forcibly disconnect a client(s) in the network.

The specific commands used in my testing after directly identifying the MAC address of a client connected to this access point is:

```bash
sudo aireplay-ng --deauth <NUMBER> -a <AP_MAC> -c <DEVICE_MAC> wlan0mon
```
* <AP_MAC> is the MAC address of the access point.
* <DEVICE_MAC> is the MAC address of the client.
* <NUMBER> is the number of times a de-authentication string is sent, setting to 0 will make it infinite.

<img width="1920" height="359" alt="image" src="https://github.com/user-attachments/assets/e2d21c46-37bd-4b3a-bca2-0dda6bfc1bfd" />

In my testing, this output ended at 5 strings as I have inputted 5 on my command, and it was enough to promptly disconnect my client device from the access point which shows that 802.11w is not a feature present in this access point as it is also not viewable for my access point configuration menus. 

## Testing Insights and Recommendations
Tests like the one showcased above highlights the importance of testing the platform as these are one of the few security tests that revealed an important consideration to have is to find/use an access point that supports 802.11w (Protected Management Frames) if we want to minimise all possible attack vectors on the Raspberry Pi.

Other recommendations were made through other testing procedures, all of which can be viewed on the technical document provided at the top of this document.
