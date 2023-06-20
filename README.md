# JetsonORINAGX_Maintenance

## Finding Jetpack verion and other related information through CLI
- Open terminal in orin and execute this
  
  ```
  sudo apt-cache show nvidia-jetpack
  ```

## Connecting Orin with USB Serial
- To connect your Laptop with Jetson Orin do the following:

#### Hardware Setup
  - Orin's DP port shouldn't be connected to any monitor
  - First connect the USB Type-A to Type-C from the host computer to Orin Type-c port(Next to 40 pin connector)
  - Now plugin the power into the Type-C(above the DC jack)
  - Your developer kit should automatically power on, and the white LED near the power button will light. If not, press the Power button.
#### Software Setup
  - Now open terminal in the host computer and type this command to find the ACM device:
    ```
    dmesg | grep --color 'tty'
    ```
  - You will get something like this
    ```
    [xxxxxx.xxxxxx] cdc_acm 1-5:1.2: ttyACM0: USB ACM device
    ```
  - The new serial device is for your Jetson developer kit
    ```
    ls -l /dev/ttyACM0
    ```
    ##### Screen command
  - Install Screen if its not installed
    ```
    sudo apt-get install -y screen
    ```
  - Use the device name displayed previously and execute this command
    ```
    sudo screen /dev/ttyACM0 115200
    ```
  - To terminate your screen session, press( Ctrl+A then K ), then press y on confirmation.
##### Internet Connection using CLI
  - As now we are in orin but we have just the terminal access so connecting to internet is only possible through wifi/ethernet.
  - For ethernet connection its pretty straight forward just plugin your ethernet cable in RJ 45 port of Orin.
  - For Wifi connection follow this article - [How to connect to WiFi through the terminal command line](https://www.linuxfordevices.com/tutorials/ubuntu/connect-wifi-terminal-command-line)

##### Errors
- If the orin isn't getting detected. Then try doing these
  1. Uplug and plug power once.
  2. Push Power button to turn off the device and then turn on by pushing it again.
  3. Still your host computer isn't detecting Orin then you have to reflash the Orin with the new Jetpack version using [SDK Manager](https://developer.nvidia.com/sdk-manager). First you need to turn on recovery mode. In order to do that
     - Connect NVIDIA Jetson AGX Orin Developer Kit to the PC with the bundled USB Type-A to Type-C cable.
     - Make sure you put the Type-C plug of the cable into the USB Type-C port next to 40-pin connector for flashing.
     - While holding the middle Force Recovery button(middle button among three of them), insert the USB Type-C power supply plug into the USB Type-C port above the DC jack. This will turn on the Jetson dev kit in Force Recovery Mode.
  
**Now go to next section in order to install newer Jetpack.**

## Flashing or Updating with a newer Jetpack
- Follow along this article - [from Ridgerun](https://developer.ridgerun.com/wiki/index.php/NVIDIA_Jetson_Orin/JetPack_5.0.2/Getting_Started/Wizard_Flashing#Step_2:_Flash)
- You can also follow the official website of Nvidia - [NVIDIA SDK Manager Documentation](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html)
  
**Note - We have Jetson AGX Orin 32 GB Developer Kit.**

## Errors while flashing Orin with SDK Manager
- You will find that after downloading the OS (New Jetson Linux) its not flashing into the orin. Its failing everytime you retry. So for that i Suggest you to try **Repair/Unistall** which you can find in the STEP 01 of SDK Manager. For more info on this go to this link - [Repair/Uninstall](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html#:~:text=complete%20the%20installation.-,2.%C2%A0Repair%20and%20Uninstall,-To%20update%20or)
- Now if you have downloaded Other SDKs too using SDK Manager and you aren't able to install it(in SDK Manager) using USB option then try Ethernet Option. Plug an Ethernet and ssh into your orin. The orin's IPv4 address can be easily found by this executing this command
```
hostname -I
```
- After that Type your login and password and it will start installing your SDKs.
