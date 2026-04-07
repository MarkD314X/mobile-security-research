</> Markdown

# Android Traffic Analysis Lab

## Objective

To generate mobile traffic from an emulated Android device with an insecure application as the destination. 
Capture the traffic with the use of tools such as Burpsuite and Wireshark. 
Analyze and document the information to identify the insecure communications. 

## Lab Environment

Emulator Configuration
Device: Pixel 8a
Android Version: 16 (API 36)
Host OS: Windows 11
Proxy: Burp Suite

## Tools Used

Android Studio
PowerShell
Burp Suite
Wireshark
ADB

## Setup

Created empty Android Studio project with emulated Pixel 8a. 
Used PowerShell to launch the emulated device. 
PS C:\Users\********> C:\Users\************\AppData\Local\Android\Sdk\emulator\emulator.exe -list-avds
Pixel_8a
PS C:\Users\************> C:\Users\***************\AppData\Local\Android\Sdk\emulator\emulator.exe -avd Pixel_8a

1. Launch emulator
2. Install AndroGoat via command line using ADB.
2. Configure proxy using Burp Suite
3. Install CA certificate

## Procedure

1. Navigate to Emulator Directory
From PowerShell: cd C:\Users\**********\AppData\Local\Android\Sdk\emulator

2. Start the Emulated Device
Launch the Android Virtual Device(AVD): Start-Process emulator -ArgumentList "-avd Pixel_8a"

3. Configure Proxy on the Emulator
Use Android Debug Bridge(ADB) to route emulator traffic through local proxy: 
adb shell settings put global http_proxy 10.5.0.2:8080

4. Start the Proxy Listener 
Launch Burp Suite and configure the proxy listener to global on port 8080:
Bind address: All Interfaces (*) 
Port: 8080
Example:  *:8080

5. Generate Network Traffic
Open browser on emulated device. Attempt to navigate to website to generate HTTP/HTTPS requests. Using OWASP Juice Shop for web traffic.

6. Capture Traffic
Observe the requests in Burp Suite.
Burp Suite -> Proxy -> HTTP history 


## Results



## Notes