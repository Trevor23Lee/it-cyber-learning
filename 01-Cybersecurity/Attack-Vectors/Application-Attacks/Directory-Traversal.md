# Directory Traversal

## Attack Vector Classification:
Application Attack

## Description:
Directory Traversal (also known as Path Traversal) is a web security vulnerability that allows an attacker to access files and directories stored outside the intended web root folder.

By manipulating file path parameters in a URL or form input—often using special sequences like ```../``` (dot-dot-slash)—the attacker can “traverse” the directory structure of the server. This can expose sensitive files such as configuration files, database credentials, password lists, or system logs that were never meant to be publicly accessible.

For example, if a web application loads files based on user input (e.g., ```https://example.com/view?file=report.txt```), an attacker might modify the parameter to ```../../etc/passwd``` to retrieve the server’s password file on a Unix system.

If the application does not properly sanitize or validate these inputs, the attacker could gain unauthorized access to critical system files, potentially leading to further exploitation.

## Common Target(s):
- Websites storing sensitive configuration files inside the web root
- Web applications that dynamically load files based on user input without validation
- Servers with misconfigured permissions allowing public access to restricted directories

## Impact:
A successful directory traversal attack can lead to:
- Exposure of sensitive files such as configuration files, passwords, or API keys
- Unauthorized access to user data or system files
- Full compromise of the underlying server if critical system files are accessed or modified

## Real-World Example(s):
[Year] – [Short description of the event and its impact.]  
*[Link to source]*

## How It Works:
Directory traversal attacks exploit insufficient input validation in web applications. The attacker looks for input fields, URL parameters, or form submissions that accept file or path information.
For example, a vulnerable site might retrieve files like this:
```https://example.com/view?file=report.txt```

If the application fails to sanitize the file parameter, the attacker can manipulate it using special path traversal sequences such as:
```https://example.com/view?file=../../../../etc/passwd```

In this case:
- ```../``` moves up one directory level.
- Repeating the sequence allows the attacker to escape the web root directory.
- The targeted file path (/etc/passwd in this example) contains sensitive system information.

If successful, the server returns the contents of the requested file. This can expose configuration files, user credentials, or even system-level files that help the attacker escalate privileges or execute further attacks.

## Tools Commonly Used:
**Hardware:**
- Any computer with access to internet

**Software:**
- ```curl``` – for sending crafted HTTP requests and retrieving server responses
- ```Burp Suite``` – for intercepting and modifying web requests to test for traversal vulnerabilities
- ```DirBuster``` – for automated directory and file discovery, including traversal attempts

## Prevention / Detection Methods:
- Validate and sanitize user input – explicitly allow only expected values, and reject sequences like ../ or %2e%2e%2f.
- Use whitelisting instead of blacklisting – define acceptable file paths and restrict access to only those.
- Enforce least privilege – configure the web server so it only has access to necessary directories, never sensitive system files.
- Disable directory listing – prevent the server from showing folder contents if no index file exists.
- Use web application firewalls (WAFs) – block known traversal patterns and suspicious requests in real time.
- Monitor logs – watch for repeated ../ requests, URL-encoded traversal attempts, or unexpected file accesses.

## Resource(s):
- [OWASP - Directory Traversal](https://owasp.org/www-community/attacks/Path_Traversal)
- [Wiki - Directory Traversal Attack](https://en.wikipedia.org/wiki/Directory_traversal_attack)
- [PortSwigger - Path Travel](https://portswigger.net/web-security/file-path-traversal)
