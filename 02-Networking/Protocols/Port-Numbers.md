# Port Numbers


## What Are Port Numbers?

Port numbers are numerical identifiers used in networking to distinguish different services or applications on a single device. They work alongside an IP address to direct network traffic to the correct application. For example, when you visit a website, your computer connects to port 80 (HTTP) or 443 (HTTPS) on the server.

Port numbers are divided into three main ranges:

1. **Well-Known Ports (0–1023):** Reserved for standard services and protocols, like HTTP (80), HTTPS (443), FTP (20-21), SSH (22), and SMTP (25). These ports are controlled and assigned by the Internet Assigned Numbers Authority (IANA).

2. **Registered Ports (1024–49151):** These ports can be registered for proprietary applications, third-party software, or user-defined services. Many applications and games use these ports for communication.

3. **Dynamic / Private Ports (49152–65535):** Also known as ephemeral ports, these are generally used for temporary client-side connections. They are assigned dynamically when a client initiates a connection and are not associated with a fixed service.


## Major Port Numbers

| Port       | Service                                      | Notes / Use Case                                  |
|------------|---------------------------------------------|--------------------------------------------------|
| 20-21      | FTP                                         | File Transfer Protocol, data & control ports     |
| 22         | SSH                                         | Secure remote login                              |
| 23         | Telnet                                      | Remote terminal access (unsecured)              |
| 25         | SMTP                                        | Sending email                                    |
| 53         | DNS                                         | Domain Name System lookups                        |
| 67-68      | DHCP                                        | IP address assignment                             |
| 69         | TFTP                                        | Simple file transfer                              |
| 80         | HTTP                                        | Web traffic                                      |
| 110        | POP3                                        | Retrieving email                                 |
| 111        | RPC                                         | Remote Procedure Calls                            |
| 123        | NTP                                         | Time synchronization                              |
| 135        | Microsoft RPC / DCOM                        | Windows service communication                     |
| 137-139    | NetBIOS                                     | Windows file & printer sharing                    |
| 143        | IMAP                                        | Email retrieval                                  |
| 161-162    | SNMP                                        | Network device monitoring                          |
| 179        | BGP                                         | Routing protocol                                  |
| 389        | LDAP                                        | Directory services                                |
| 443        | HTTPS                                       | Secure web traffic                                |
| 445        | SMB / Microsoft-DS                          | File and printer sharing                          |
| 465        | SMTP over SSL                               | Secure email sending                               |
| 514        | Syslog                                      | Logging service                                   |
| 520        | RIP                                         | Routing Information Protocol                       |
| 548        | AFP                                         | Apple File Protocol                                |
| 587        | SMTP (Message Submission)                   | Email sending                                     |
| 631        | IPP                                         | Network printing                                   |
| 636        | LDAPS                                       | Secure LDAP                                       |
| 989-990    | FTPS                                        | FTP over SSL                                      |
| 993        | IMAPS                                       | Secure email retrieval                             |
| 995        | POP3S                                       | Secure POP3 retrieval                              |
| 1080       | SOCKS Proxy                                 | Proxy protocol                                    |
| 1194       | OpenVPN                                     | VPN connections                                   |
| 1433       | Microsoft SQL Server                         | Database service                                  |
| 1434       | Microsoft SQL Monitor                        | SQL monitoring                                    |
| 1521       | Oracle Database                              | Database service                                  |
| 1723       | PPTP                                        | VPN connections                                   |
| 1812-1813  | RADIUS                                      | Authentication / accounting                        |
| 2049       | NFS                                         | Network File System                               |
| 2082       | cPanel                                      | Web hosting control panel                          |
| 2083       | cPanel over SSL                              | Secure web hosting control panel                  |
| 2086       | WHM                                         | Web Host Manager                                   |
| 2087       | WHM over SSL                                 | Secure WHM                                       |
| 3306       | MySQL                                       | Database service                                  |
| 3389       | RDP                                         | Windows Remote Desktop                             |
| 3689       | DAAP                                        | Digital Audio Access Protocol                      |
| 4369       | Erlang Port Mapper                           | Internal service                                   |
| 5432       | PostgreSQL                                  | Database service                                  |
| 5900       | VNC                                         | Remote desktop                                    |
| 5985       | Windows Remote Management (HTTP)            | Remote management                                 |
| 5986       | Windows Remote Management (HTTPS)           | Secure remote management                           |
| 8080       | HTTP Alternate / Proxy                       | Web proxy or alternative HTTP port                |
| 8443       | HTTPS Alternate / Admin Console             | Web administration / secure alternative HTTPS    |
