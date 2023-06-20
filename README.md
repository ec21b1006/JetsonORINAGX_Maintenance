# JetsonORINAGX_Maintenance

## Connecting Orin with USB Serial
- To connect your Laptop with Jetson Orin do the following:

#### Hardware Setup
  - Orin's DP port shouldn't be connected to any monitor
  - First connect the USB Type-A to Type-C from the host computer to Orin Type-c port(Next to 40 pin connector)
  - Now plugin the power into the Type-C(above the DC jack)
  - Your developer kit should automatically power on, and the white LED near the power button will light. If not, press the Power button.
  - Now open terminal in the host computer and type this command to find the ACM device:
    ```
    dmesg | grep --color 'tty'
    ```
    
