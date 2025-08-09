# nmap

[nmap photo](../../../13-Personal/Images/Nmap-1024x535.png)

**Synopsis:** nmap[scan type][options]{target specification}

## What is nmap?

nmap, also known as a network mapper, which is used for port scanning and vulnability analysis. You can find live hosts, open ports, services, and operating systems on a network. 


## Common uses:
- Discover devices on a network
- Scan for open TCP/UDP ports
- Detect running services and versions (e.g., SSH, HTTP)
- Attempt OS fingerprinting
- Identify firewall rules and configurations
- Perfrom vulnability assessments (with scripts)

---

## Where it's useful:
- Home lab testing, checking your own network
- Penetration tests
- Pre-engagement reconaissance

---

## The Six Port States:
1. open: actively accepting TCP connections, UDP datagrams or SCTP associations on this port
2. closed: Is accessible (recieves and responds to nmap probe packets), but there is no applications on this port
3. filtered: nmap cannot determine whether port is open because packet filtering prevents its probes from reaching the port
4. unfiltered: Port is accessible, but nmap is unable to determine whether it is open or closed
5. open|filtered: Unable to determine whether port is opened or filtered
6. closed|filtered: Unable to determine whether port is closed or filtered

---

Basic Commands:
- Scan a single IP: ```nmap 10.0.0.2```
- Ping scan (find local hosts on a network): ```nmap -sn 10.0.0.2/24```
- Scan multiple IPs: ```nmap 10.0.0.97 10.0.0.2 10.0.0.255```
- Port scan: ```nmap -p 22,80,443 10.0.0.97```
- Full TCP port scan: ```nmap -p- 10.0.0.97```
- Manual on how to use and options of nmap: ```man nmap```

---

## Most useful commands



---

## Scripting

---

## Resources

- [nmap cheatsheet](https://www.stationx.net/nmap-cheat-sheet/)
- [nmap documentations](https://nmap.org/docs.html)