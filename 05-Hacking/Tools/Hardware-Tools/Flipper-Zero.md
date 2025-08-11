# Flipper Zero

![Flipper Zero](../../../13-Personal/Images/Flipper-Picture.png)

**Where to buy:** [Flipper Zero](https://flipperzero.one/)

---

## What is a Flipper Zero Device?

The Flipper Zero is a compact and portable multi-tool designed for pentesters, cybersecurity enthusiasts, hackers, and hobbyists interested in hardware hacking or tech pranks. It integrates multiple radio protocols, GPIO pins, infrared control, RFID/NFC capabilities, and more into a single handheld device with an intuitive interface. When you get a physical Flipper Zero, it comes with the base firmware available from the official [Flipper Zero Website](https://flipperzero.one/downloads). Alternatively, you can install third-party firmware like [Momentum](https://momentum-fw.dev/) which I personally use—it enhances the original firmware by adding extra tools and games. You can update or manage your device firmware using qFlipper, available for Windows, macOS, and Linux, or through the official mobile app available on the Apple App Store and Google Play Store.

## Common Uses:
- Radio frequency (RF) signal sniffing and replay (e.g., garage remotes, car keys)
- RFID and NFC tag reading, emulation, and cloning
- Infrared remote control emulation
- GPIO pin interaction for hardware debugging and hacking
- Signal jamming and fuzzing
- Storage of scripts and payloads for quick deployment
- Game device

## Where it's useful:
- Physical security assessments and penetration tests
- IoT device testing
- Wireless protocol research and exploitation
- Hobbyist projects and learning hardware hacking
- Tech pranks and demonstrations

---

## The Features in detial:

### Radio Frequency Identification (RFID):
This tool is used to scan low-frequency proximity cards nearby. This type of card is used in multiple cases throughout the world, from hospital badges to get into building, geotags, pet chips, merchandise, and various other uses. These RFIDs store only N-byte ID and has no authentication mechanism. Which allows it be read, cloned and then emulated by anyone with a device like the Flipper Zero. 
With the Flipper Zero device, all that is needed is to turn on the ```read``` mode, hold it near a RFID, which the device has a 125 kHz antenna to read. The interface will show that it is trying to read the RFID. Once it reads and gains the information of the RFID, you are allowed to save it or not. The device is able to store multiple RFIDs, to where the user can then emulate the RFID signal to gain access into buildings or simulate the signal.

### Near Field Comminication (NFC):
This tool is similar to the RFID tool, but allowing to gain information from a NFC-enabled devices. NFC-enabled devices are also used heavily now, usually associated with payments. These devices are embedded in your phones, smart watches, and credit/debit cards, where one uses it to pay for items. 
Again with the Flipper Zero, you are able to hold near a NFC device like a debit card, read the information off of it. Which you only gain most of the information, not all of it, like the CVV. Then after recieving the information, you can save it and then later emulate it. 

### Sub-GHz Radio:
The Sub-GHz tool allows the Flipper Zero to receive and transmit signals in common frequency ranges such as 315, 433, 868, and 915 MHz. These frequencies are widely used by wireless key fobs, garage door openers, remote-controlled devices, and certain IoT gadgets. With the built-in antenna, the Flipper can capture a signal, save it, and replay it later to perform the same action as the original transmitter.  
To use this feature, you can select the "Read" mode, press a compatible remote near the device, and let it capture the transmission. The interface will indicate the frequency and modulation detected. Once saved, the Flipper can then transmit the same signal to control the target device. This function is heavily dependent on local laws and should only be tested on devices you own or have explicit permission to operate.

### Infrared:
The Infrared tool in the Flipper Zero works much like a universal remote control. It allows the device to send and store IR signals used by TVs, air conditioners, projectors, and other appliances that rely on infrared communication.  
To capture a signal, switch the Flipper into "Learn" mode and point the existing remote toward the IR sensor located at the top of the device. Once the button is pressed on the remote, the Flipper records the IR pattern, which can then be saved under a custom name. Later, you can select that saved entry and transmit it, effectively controlling the original device without the physical remote. The Flipper also comes with a preloaded IR database for common devices.

### GPIO:
The GPIO (General-Purpose Input/Output) interface allows the Flipper Zero to interact directly with other hardware through its onboard pins. These can be used to send or receive digital signals, power external circuits, or communicate using protocols like UART, SPI, and I²C.  
Users can connect wires to the GPIO pins and control them through the Flipper’s interface, enabling testing of hardware devices, reading sensor outputs, or automating button presses. With the right configuration, it can be used for device debugging, prototyping, or triggering actions on custom electronics.

### USB / Bad KB:
The USB HID (Human Interface Device) or "Bad KB" mode enables the Flipper Zero to emulate a keyboard or mouse when plugged into a computer. This allows the device to automatically type commands, open applications, or execute prewritten scripts at high speed.  
By loading a payload file in DuckyScript or a similar scripting language, you can automate complex sequences for penetration testing or system administration tasks. For example, you could script the device to open a terminal, run network diagnostic commands, and save the output. As with all features, this should only be used on systems where you have explicit authorization.

### iButton:
The iButton tool lets the Flipper Zero read, store, and emulate Dallas Semiconductor 1-Wire keys, often found in older access control systems, vending machines, and time-tracking devices. These keys are small metal contacts that transfer data when touched to a reader.  
With the Flipper’s iButton interface, you can touch the key to the designated contact pad, read its unique ID, and save it. Later, the Flipper can emulate the key, granting the same level of access as the original. This is especially useful for replacing lost keys in systems you are authorized to access.

### U2F:
The U2F (Universal 2nd Factor) application turns the Flipper Zero into a hardware security token for online authentication. U2F is commonly used for two-factor authentication (2FA) to protect accounts from unauthorized access.  
When enabled, the Flipper can register as a security key with services that support the U2F standard. During login, instead of entering a code, you simply plug in the Flipper, press the confirmation button, and it securely transmits a cryptographic challenge/response. This feature is legitimate and safe to use on your own accounts for enhanced security.

### Video Games:
The Flipper Zero also includes several simple built-in games such as Flappy Bird, 2048, Blackjack, and others. These games provide entertainment during downtime and showcase the device’s interactive screen and controls. While not directly related to pentesting or hacking, they add to the device’s versatility and user experience.


### Other Tools/Uses:
Beyond the built-in features, the Flipper Zero has a thriving community that creates additional tools and utilities. Examples include a resistor color code calculator, physical key pattern copier, password generator, and many more handy utilities that expand the device’s functionality.  
With the GPIO interface, various hardware add-ons are available, including a Wi-Fi enabled expansion board. This Wi-Fi module allows the Flipper Zero to perform advanced wireless attacks such as man-in-the-middle (MITM) attacks or Wi-Fi deauthentication attacks that can disconnect devices from a network. These extensions make the Flipper an even more powerful tool for wireless security testing and research.

---

## My experience with this device:
I recently acquried this device a few months ago on the intent of learning about how one can hack into various technologies. I have even shown this device to multiple friends and family, as to show them that these devices are out there and be aware. I showed and talked about the various uses to them to educate them, hoping to make them more alerted and enforce security to not be affected by a device like this. When I got the device, I also acquired the WiFi enabled GPIO add-on board to do more attacks related to WiFi. I have tested and played around with most of the tools on there, from scanning my credit card to turning on my TV/Fans. It is a fun little device but has limitations on what you can do. I have researched that this device is a small endevor to the vast amount of hacking devices out there, like the [WiFi Pineapple](https://shop.hak5.org/products/wifi-pineapple?variant=81044992). I did learn a few things while experiencing this device in person rather than reading about it. I also did enjoy educationing people on this device, to both educate them and scare them a little. 

---

## Knowledge factor:
**8/10**
I am confident in my understanding of the main tools available on the Flipper Zero and how they are applied in various scenarios. I have explored each tool through hands-on penetration testing, including my credit card (NFC), TV and fans (Infrared), school badge (RFID), USB Rubber Ducky emulation on a laptop (USB/Bad KB), Wi-Fi attacks using the GPIO Wi-Fi add-on, and even playing some of the built-in games. However, there are still a few features I haven’t fully tested or mastered, particularly regarding simulating real-world attacks.

## Disclaimer:
The Flipper Zero is intended solely for educational purposes, personal security testing, and <ins>authorized</ins> research. Use of this device must always be **legal** and ethical. You should only test devices, systems, or networks that you own or have explicit written permission to assess. Never operate the Flipper Zero in public or on systems without consent, as unauthorized use may violate laws and regulations.

