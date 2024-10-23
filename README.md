# IPv6Spot Project

> The IPv6Spot project is an open-source, free system with the goal to advance the development of IPv6.

> Note: Companies interested in purchasing a license to use the source code commercially can contact this number on WhatsApp: +90 537 450 65 16

## Quick Start

### Installation Guide
- [Video Installation Guide](https://youtu.be/Iejz8vUP9wY?si=NBwTcxjhvVZ8RIn_)
- [ISO File Download](https://drive.google.com/file/d/1aDe7ILiZPsQL_ZeCsoAG2Kg7vWE2YxC3/view?pli=1)

## Support the Project 🙏🏻💚

Support our 'ipv6spot' project to secure public Wi-Fi with IPv6. Every contribution helps.

**Bitcoin Wallet:**
```
17w2iiZevtWzRyQeSYhrBWrhCyQmKBqzVx
```

## Project Information

- **Project Start Date:** 06/2021
- **License:** MIT License (See [LICENSE](./LICENSE) file)
- **Contact:** abdulkader.alrezej@outlook.com

**Important Note:** The IPv6 addresses used in the source code are examples only. You must replace them with addresses compatible with IPv6 standards.

## Research Paper

### IPv6Spot - An Innovative IPv6 Captive Portal Solution with Integrated DNS and Proxy Services

#### Abstract
This paper introduces IPv6Spot, a pioneering captive portal system designed exclusively for IPv6 networks. Developed by Abdulkader Alrezej, IPv6Spot addresses the critical need for effective network access control in IPv6 environments. The system offers comprehensive features such as user authentication, dynamic IP and MAC address management, bandwidth control, usage monitoring, integrated DNS redirection, and custom proxy servers.

#### Introduction

The global transition to IPv6 is necessitated by the exhaustion of IPv4 addresses and the growing number of internet-connected devices. Despite this shift, many network management tools and captive portal solutions remain focused on IPv4, leaving a gap in support for IPv6 networks. IPv6Spot fills this gap by providing a fully functional captive portal tailored for IPv6 environments.

#### Project Overview

IPv6Spot is a Python-based application utilizing the Flask web framework, various Linux networking utilities, a custom DNS server, and proxy servers. Key features include:

1. IPv6 Captive Portal with DNS and Proxy Redirection
2. Secure User Authentication
3. Dynamic IP and MAC Address Management
4. Bandwidth Control and Traffic Shaping
5. Usage Monitoring and Enforcement
6. Custom DNS and Proxy Server Integration

#### System Architecture

The architecture of IPv6Spot is modular, comprising several interconnected components that work together to manage network access and enforce policies.

##### Web Interface
- **Flask Framework:** Manages HTTP requests, user sessions, and renders templates for the web interface
- **Templates and Static Files:** Provide the user interface elements such as login pages and dashboards

##### Networking Layer
- **IP and MAC Address Management:** Utilizes system commands and the ipaddress module to manage IPv6 addresses and associate them with user sessions
- **Traffic Control:** Implements bandwidth limitations and traffic shaping using the tc command
- **Firewall Rules:** Uses ip6tables and nftables to enforce network access policies

##### Database Layer
- **SQLite Database:** Stores user credentials, session data, IP addresses, and usage statistics
- **Schema Management:** Ensures the database schema supports all required fields for new features

##### Custom DNS Server
- **DNS Interception:** A DNS server built with the dnslib library intercepts DNS queries from clients
- **Domain Redirection:** Redirects specific DNS queries to the captive portal or blocks them based on the client's authentication status
- **IPv4-to-IPv6 Translation:** Converts IPv4 addresses to IPv6 format for domains that do not have IPv6 records

##### Custom Proxy Servers
- **HTTP Proxy Server:** Intercepts HTTP requests from clients and redirects unauthenticated users to the captive portal
- **Network Detection Responses:** Provides appropriate responses to network connectivity checks performed by operating systems

##### Background Services
- **Periodic IP Checks:** Monitors user activity and enforces policies through background threads
- **Usage Data Collection:** Continuously updates usage statistics

#### Implementation Details

The implementation of IPv6Spot involves integrating Python scripts with system-level networking commands, a custom DNS server, and custom proxy servers.

##### User Authentication
- **Credential Security:** Uses werkzeug.security for password hashing and verification
- **Session Handling:** Manages user sessions securely using Flask's session management and secret keys

##### IP and MAC Address Management
- **MAC Address Retrieval:** Executes ip -6 nei to map IPv6 addresses to MAC addresses
- **Dynamic IP Handling:** Adds or removes IPv6 addresses in nftables based on user authentication status

##### Traffic Control
- **Bandwidth Allocation:** Creates tc classes and filters to enforce per-user bandwidth limits
- **Dynamic Adjustment:** Updates tc rules in response to changes in user sessions

#### Features and Functionality

##### Enhanced Captive Portal with DNS and Proxy Redirection
- **User Experience:** Improves the captive portal by intercepting DNS and HTTP requests, ensuring users are prompted to authenticate
- **Seamless Integration:** The DNS and proxy servers work in conjunction with firewall rules to control network access effectively

##### Secure Authentication and Authorization
- **Password Security:** Implements secure password storage and verification
- **Session Binding:** Associates sessions with specific IP and MAC addresses to prevent session hijacking

##### Dynamic Network Management
- **Automatic IP Assignment:** Dynamically assigns IPv6 addresses to users upon authentication
- **Device Recognition:** Identifies devices based on MAC addresses, allowing for device-specific policies

#### Results and Testing

IPv6Spot has been tested extensively to validate its functionality and performance:

- **Functional Testing:** Confirmed that the DNS and proxy servers correctly intercept and redirect queries and requests based on user authentication status
- **Performance Testing:** Ensured that the servers handle queries and requests efficiently without introducing significant latency
- **Security Testing:** Tested against various attack vectors, including DNS spoofing and unauthorized access attempts
- **Compatibility Testing:** Verified that the system operates correctly with different client devices and operating systems supporting IPv6

#### Future Work

Potential enhancements to IPv6Spot include:

- **Advanced DNS Features:** Implement DNSSEC validation and support for more complex DNS query types
- **Enhanced Proxy Capabilities:** Incorporate HTTPS interception and support for additional protocols
- **Integration with Security Platforms:** Incorporate intrusion detection and prevention systems
- **Scalability Improvements:** Optimize the system for larger networks with higher user volumes
- **User Interface Enhancements:** Develop a more intuitive web interface with responsive design
- **Multi-Language Support:** Localize the user interface to support multiple languages

#### Acknowledgments

This project was developed by Abdulkader Alrezej, whose expertise and dedication have led to the creation of IPv6Spot. Special thanks to the developers and maintainers of open-source projects such as Flask, dnslib, SQLite, and Linux networking utilities, which were instrumental in developing this solution.

#### References

1. Hagen, Silvia. IPv6 Essentials. O'Reilly Media
2. Flask Documentation. Flask
3. dnslib Documentation. dnslib
4. SQLite Documentation. SQLite
5. The Linux Foundation. Linux Advanced Routing & Traffic Control HOWTO
6. Netfilter Project. nftables
7. Python Documentation. subprocess Module
8. Python Documentation. http.server Module

#### Appendix: Detailed Code Analysis

To provide a deeper understanding of IPv6Spot, we include an analysis of the key components and functions in the source code related to the custom proxy servers.

##### Custom Proxy Servers
The proxy servers are designed to intercept HTTP requests and provide appropriate responses to enhance the captive portal functionality.

##### Proxy Server for Unauthenticated Users
Purpose: Redirects all HTTP GET requests to the captive portal login page for unauthenticated users.

**Implementation:**
```python
# Class Definition: Inherits from http.server.SimpleHTTPRequestHandler
# do_GET Method: Overrides the default GET request handler
# Server Setup: Uses socketserver.ThreadingTCPServer with socket.AF_INET6
```

**Features:**
- Stateless Handling: Does not maintain any state between requests, ensuring scalability
- Logging: Overrides log_message to suppress unnecessary logging

#### Conclusion

IPv6Spot represents a significant advancement in IPv6 network management tools. Its comprehensive approach to network access control, combined with innovative DNS and proxy services integration, provides a robust solution for modern network environments. The project's open-source nature and modular architecture create opportunities for further development and adaptation as IPv6 adoption continues to grow.

## Installation Requirements

### Directory Structure
Main File Directory: `/mnt/cerr`

```
/mnt/cerr/
├── db/         # Database encryption and backup files
├── web_dist/   # Web Dashboard Pages Files
├── console/    # Create virtual interfaces for IPv6Spot
├── daa/        # Main system database Sqlite3
├── external_domains/ # Site blocking configuration
├── sn/         # DNS server
├── tba/        # nftables rules file
├── tv/         # IPv6Spot system
├── wb/         # Back-End of web control panel
├── xt/         # IPv6Spot Web Proxy A (Captive portal detection URLs)
└── xtt/        # IPv6Spot Web Proxy B (Respond to detection URLs)
```

### System Requirements
- OpenWRT 22.03.0
- Kernel Version: 5.10.138
- Python 3.10.13
- Scapy 2.5.0

### Required OpenWRT Packages
```
NAT64 for IPv6-only network (Jool)
conntrack
python3-lzma
python3-multiprocessing
python3-ncurses
python3-openssl
python3-pillow
python3-pip
python3-pkg-resources
python3-ply
python3-psutil
python3-pycparser
python3-pydoc
python3-readline
python3-setuptools
python3-sqlite3
python3-unittest
python3-urllib
python3-uuid
python3-xml
python3
python3-asyncio
python3-base
python3-bidict
python3-cffi
python3-cgi
python3-cgitb
python3-codecs
python3-ctypes
python3-dbm
python3-decimal
python3-dev
python3-distutils
python3-email
python3-lib2to3
python3-light
python3-logging
tc-full
tc-mod-iptables
sqlite3-cli
libsqlite3-0
ip6tables
nftables
xtables-nft
kmod-ip6tables
ip-full
iputils-arping
nmap
kmod-veth
```

### Python Dependencies
```
aiodns==3.2.0
aiohttp==3.9.5
aiosignal==1.3.1
altgraph==0.17.4
annotated-types==0.7.0
anyio==4.4.0
APScheduler==3.10.4
arabic-reshaper==3.0.0
async-timeout==4.0.3
asyncio==3.4.3
attrs==23.2.0
bcrypt==4.2.0
bidict==0.21.2
blinker==1.8.2
cachelib==0.13.0
cachetools==5.5.0
certifi==2024.7.4
cffi==1.16.0
chardet==5.2.0
charset-normalizer==3.3.2
click==8.1.7
dnslib==0.9.25
dnspython==2.6.1
[...remaining pip dependencies preserved...]
```

### Installation Steps

1. Disable Dnsmasq

2. Grant executable permissions:
```bash
chmod +x sn.py tv.py wb.py xt.py xtt.py
```

3. Update nftables configuration:
   - Edit `/etc/init.d/nftables`
   - Replace `nft -f /etc/nftables.conf` with `nft -f /mnt/cerr/tba`

4. Configure boot services:
```bash
procd_open_instance
procd_set_param command /mnt/cerr/xt.py
procd_set_param respawn
procd_close_instance

procd_open_instance
procd_set_param command /mnt/cerr/xtt.py
procd_set_param respawn
procd_close_instance

procd_open_instance
procd_set_param command /mnt/cerr/tv.py
procd_set_param respawn
procd_close_instance

procd_open_instance
procd_set_param command /mnt/cerr/sn.py
procd_set_param respawn
procd_close_instance

procd_open_instance
procd_set_param command /mnt/cerr/wb.py
procd_set_param respawn
procd_close_instance
```

## Testing 

### Screenshots of IPv6Spot v1.0

![ipv6spot1](https://github.com/user-attachments/assets/365bd93b-3215-4dc4-a524-3aee471cd5b3)

![ipv6spot2](https://github.com/user-attachments/assets/e94f0e85-4415-45cd-8cf5-084551bf5af5)

![7](https://github.com/user-attachments/assets/79c265fb-62a2-4200-b3f1-14415ce53b56)

![2](https://github.com/user-attachments/assets/34a387aa-9e23-4189-8301-a6757ee1d4db)

![12](https://github.com/user-attachments/assets/45ebba16-48eb-4563-9fb5-2a3c95784e97)

![image](https://github.com/user-attachments/assets/ad4ddee7-d3ac-4890-ba4d-de327a4b538e)

![image](https://github.com/user-attachments/assets/a8b6f84c-f7e4-4fa8-8498-bd6e46483806)

![image](https://github.com/user-attachments/assets/e84f0b67-721d-407e-a781-6e7d22c95ee8)

![image](https://github.com/user-attachments/assets/73825639-20d3-4587-b2ce-6bb330119bfc)

![image](https://github.com/user-attachments/assets/b0b48ab3-11c0-4a24-a6ed-9638745efd8c)

![image](https://github.com/user-attachments/assets/52664fb1-8e9f-47df-8c87-8b14ac064068)

![image](https://github.com/user-attachments/assets/146386af-59f0-43a7-9c1f-849a783d50b5)

![image](https://github.com/user-attachments/assets/d689a092-0a67-4dac-bc2f-f1f85d9fc850)

![image](https://github.com/user-attachments/assets/ef1a700b-24eb-4415-ae30-8b7876b17452)

![image](https://github.com/user-attachments/assets/17d956a3-89dd-4a9f-9c45-e415b6d753ba)

![image](https://github.com/user-attachments/assets/9a9fc9aa-91e7-478b-921d-72fbc8863e73)

![image](https://github.com/user-attachments/assets/62dfb250-58d6-400b-b0d6-bf6c79758aea)

![image](https://github.com/user-attachments/assets/097ce47c-0a64-4d2e-9b2a-d90cb052daa6)

![dns](https://github.com/user-attachments/assets/6ab21f94-648b-499e-99c2-361ee43c32a2)

![w3](https://github.com/user-attachments/assets/caee1d69-a01e-40fd-86db-cc7bc13523af)

Please report any installation or operation errors for guide improvements.
