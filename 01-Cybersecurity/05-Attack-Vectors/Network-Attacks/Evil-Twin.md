# Evil Twin Attack


## Attack Vector Classification:

Network and Social Engineering Attack


## Description:

An evil twin is a malicious, fake service or website designed to trick victims into revealing sensitive information. Hackers can set up a rogue network server (often disguised as public Wi-Fi) and load it with a script that hosts this false website.

For example, a hacker might create a network named "Starbuck's Free Wi-Fi". This network runs a payload script—often written in HTML—that imitates the official Starbucks login page for “free” internet access. When a victim at Starbucks sees and connects to this fake network, the script triggers and displays the imitation login page.

The attacker can configure the page to request any information, such as the victim’s name, but often it’s designed to capture login credentials like an email address and password. From the victim’s perspective, they enter their information and click “Enter,” but the page doesn’t actually grant internet access—because it’s not a legitimate network.

On the attacker’s side, the submitted information is captured by the script. With the victim’s email and password, the hacker can log into their account, lock them out, read their emails, and potentially gain access to other linked accounts.


## Common Target(s):

- Public WiFi locations where people expect and need free internet without asking questions of source (e.g., Coffee Shops, Airports, Hotels, etc.)
- Coroperate Environments where employees connect to office WiFi (e.g., Hospitals, banks, etc.)
- Universities and schools where open WiFi is common and login portals are expected
- Transit Hubs where travelers seek quick connections (e.g., Train stations, Cruise ships, etc.)
- High-traffic events (e.g., Concerts, Fesitvals, Sporting Events, etc.)


## Impact:

The severity of an Evil Twin attack largely depends on who the victim is and what accounts are tied to the credentials they entered. If the victim’s email is connected to sensitive systems or valuable personal data, the damage can be significant.

For example, if a CEO of a large corporation enters their corporate email and password, an attacker could gain access to:
- Confidential company documents and communications
- Sensitive business deals or merger information
- Bank transfer approvals and financial records
- Executive-level login credentials for internal systems
- Contact lists for other high-value targets (spear phishing)

Even for non-executives, the attacker could still:
- Reset passwords for multiple accounts linked to the email
- Access personal information, such as addresses and phone numbers
- Monitor communications for intelligence gathering
- Steal payment details from linked accounts
- Impersonate the victim for further attacks

In short, the impact ranges from mild inconvenience to catastrophic corporate breach, depending on the value of the compromised account.


## Real-World Example(s):

In 2020, the Interior Department’s Office of Inspector General (OIG) conducted a security test in which its red team successfully compromised the agency’s internal network using the Evil Twin attack vector. Armed with only $200 worth of publicly available equipment and open-source software, the team set up rogue Wi-Fi access points that mimicked legitimate department networks.

Employees unknowingly connected to these fake networks, allowing the team to capture login credentials and gain access to sensitive internal systems. This test revealed significant vulnerabilities in the department’s wireless security and demonstrated how a low-cost, easily executed attack could breach a major U.S. government agency.

*[Link to story](https://www.nextgov.com/cybersecurity/2020/09/interior-ig-team-used-evil-twins-and-200-tech-hack-department-wi-fi-networks/168521/)*


## How it works:

First, a hacker needs to acquire the necessary hardware and software for this attack. For hardware, there are various options, one of the most popular being the [Flipper Zero](../../05-Hacking/Tools/Hardware-Tools/Flipper-Zero.md) device. The Flipper Zero is designed for pentesting and hacking, with multiple functionalities that make it suitable for this type of operation. 

For software, the hacker needs multiple packages: one to create and emulate the rogue access point, one to serve the fake portal script, and one to handle information capture. These can sometimes be bundled into a single package, such as the [Marauder](https://lab.flipper.net/apps/esp32_wifi_marauder) Tool, which contains all the necessary software components. However, the hacker will still need to download or create a custom script for the fake portal. Below is an example of a fake login portal interface from [kleo on Github](https://github.com/kleo/evilportals/tree/master/portals/facebook-login).

![Facebook Script Interface]()

Once the hacker has all the tools in place, the next step is target planning and reconnaissance. The attacker must research the target to determine the best approach for social engineering and to customize the fake portal. For example, if the target is a laboratory called “Zero Five Lab,” the hacker would check if the lab already provides a free internet login portal. If not, they can create a portal that looks official and trustworthy. The hacker then positions themselves near the building so the victims’ devices can detect the rogue Wi-Fi signal.

When a victim connects to this fake network, they are directed to the login portal, which is entirely fake. The victim enters their email address and password, then presses “Enter.” From the victim’s perspective, nothing unusual happens—they cannot access the internet. Meanwhile, the hacker receives the credentials submitted by the victim. Multiple victims may attempt to log in, providing the hacker with a growing log of account information.

With this data, the hacker now has full access to the victims’ accounts while the victims remain unaware that anything has happened. The attacker can use the stolen credentials to access email accounts, gather sensitive information, impersonate the victims, or even lock them out of their accounts. 


## Tools Commonly Used:

Hardware:
- Flipper Zero
- Raspberry Pi

Software:
- Marauder 


## How To Prevent/Detection Methods:

- Avoid connecting to public WiFi as much as possible
- Avoid unsecured WiFi hotspots, use your own if needed
- Verify any security warnings or confirm with the organization whether the network you are connecting to is legitimate and properly secured.
- Disable Auto-connect
- [HTTPS](../Definitions.md) websites are secured
- If you suspect you’ve entered credentials on a fake portal and notice no response after hitting “Enter,” immediately change your password or lock your account to prevent the attacker from gaining access.
- Look for typos, missing logos, broken links, or any unusual elements that might indicate a fake portal.
- Verify the Wi-Fi network name carefully, checking for typos or suspicious additions (e.g., “FREE AND FAST INTERNET FOR 05LAB”) before connecting.

## Resources: 
- [Evil Twins attacks and how to prevent them](https://usa.kaspersky.com/resource-center/preemptive-safety/evil-twin-attacks)
- [Wiki for Evil Twin](https://en.wikipedia.org/wiki/Evil_twin_(wireless_networks))