# Smart Campus Wireless Network Design & Simulation

I designed and simulated a robust, secure "Smart Campus Network" to transition a university from a restricted legacy wired infrastructure to a flexible, mobile-first wireless environment. Using Cisco Packet Tracer, I modeled a hierarchical topology that provides seamless roaming, encrypted administrative management, and centralized intranet services without compromising on network security.

##  Key Features & Solutions

* **Secure Wireless Mobility:** Deployed 7 Access Points across distinct campus zones (Hostels, Academic Blocks, Library) implementing WPE (WPA2-PSK) security to ensure only authorized devices can authenticate and connect to the network.
* **Encrypted Remote Management:** Hardened network infrastructure by actively replacing plain-text Telnet with Secure Shell (SSH v2 using 1024-bit RSA keys), ensuring all administrative traffic to the routers is fully encrypted.
* **Centralized Server Farm:** Designed and configured a dedicated subnet for campus services, successfully deploying DNS, Web (HTTP), and Email (SMTP/POP3) servers for reliable intranet resource access.
* **Hierarchical Traffic Segmentation:** Built a logical topology using static routing (IPv4) and strict Class C IP subnets to cleanly segment user traffic between the Core Router, Academic Zones, and Hostel Zones.

##  Technologies & Hardware Simulated

* **Simulation Environment:** Cisco Packet Tracer (v8.2)
* **Hardware Models:** Cisco 1941 Integrated Services Routers, Cisco 2960-24TT Layer 2 Switches, Generic Cisco Access Points
* **Network Protocols:** IPv4 Static Routing, SSH v2, WPA2-Enterprise, DHCP, DNS, HTTP, ICMP
* **Concepts:** IP Address Management (IPAM), Layer 1 to Layer 3 Troubleshooting, Network Topology Design

##  How to Run and Test

1. Clone this repository and open `Campus_Network.pkt` using Cisco Packet Tracer.
2. Wait a moment for the STP to converge (ensure link lights turn green).
3. **Test Web Services:** Open a PC in the Academic Block, navigate to the web browser, and access the simulated university portal via the DNS name or directly via IP `192.168.2.4`.
4. **Test End-to-End Routing:** Open the command prompt on a Hostel PC and ping the server farm: `ping 192.168.2.4`.
5. **Test Secure Admin Access:** From an IT Consulting PC terminal, verify SSH encryption to the core router using: `ssh -l admin 192.168.2.1`.

##  Technical Hurdles & Lessons Learned

Building this simulation from scratch provided massive hands-on experience with real-world networking challenges:

* **Security by Design:** I learned that implementing security protocols (SSH, WPA2) must be done at the foundational design stage. Attempting to retrofit security onto an open network later breaks existing active connections.
* **Systematic Troubleshooting (OSI Model):** When my initial ICMP packets failed during PDU testing, I learned to strictly verify Layer 1 (checking for incorrect cable types like copper straight-through vs. cross-over, or shutdown interfaces) before attempting to debug Layer 3 routing tables.
* **Strict IP Allocation:** Managing over 20 end devices taught me the critical importance of maintaining a Master IP Table to prevent overlapping IP assignments across different subnets and DHCP pools.
