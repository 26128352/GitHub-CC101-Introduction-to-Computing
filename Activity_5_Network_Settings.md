# CC 101 – Introduction to Computing

**Republic of the Philippines**
**Sorsogon State University**
**College of Information and Communications Technology – Bulan Campus**
Zone 8, Bulan, Sorsogon | Tel. No.: 056 311-0103 | Email: cict@sorsu.edu.ph

## "Know Your Network Settings": Exploring Windows 11 Network Configuration Tools

| | |
|---|---|
| **Name** | Julius B. Banalnal |
| **Block** | BSCS 1-1 |
| **Computer Unit Used (Desktop/Laptop, brand)** | ASUS Vivobook Go 15.6-inch FHD (AMD Ryzen 3 7320U, 8 GB RAM, 128 GB SSD) |
| **Date** | October 19, 2026 |

---

## I. Objectives

At the end of this activity, you should be able to:

- Locate network adapter information using Windows 11 Settings, the Control Panel, Command Prompt (CMD), and PowerShell.
- Use `ipconfig`, `getmac`, `hostname`, `ping`, `netstat`, `route print`, and `systeminfo` in CMD, and `Get-NetAdapter`, `Get-NetIPAddress`, and `Test-Connection` in PowerShell.
- Interpret a sample `ipconfig /all` output from a networked computer: identify its IP address, subnet mask, default gateway, and DNS servers, and classify the address as public or private.
- Relate each tool and finding to the layer of the OSI model where it works.
- Design a simple network and IP address plan for the computer laboratory.

## II. Materials Needed

- A computer running Windows 11 (a network or Internet connection is **not** required for this activity)
- This worksheet (printed copy, or the digital file to fill out and submit)
- Week 6 lecture notes, for reference on IP addresses, protocols, the OSI model, and network devices

## III. Background

A computer does not need to be connected to a network to have network settings. Every PC has one or more **network adapters** (NICs), each with a permanent **MAC address**, and Windows always runs the TCP/IP software, including the **loopback** address 127.0.0.1 (IPv4) and ::1 (IPv6) that the computer uses to talk to itself. Windows 11 lets you inspect these settings in four places: the **Settings** app, the classic **Control Panel**, **Command Prompt (CMD)**, and **PowerShell**. In this activity, you will explore all four on your own unit, observe how Windows behaves when no network is available, and then analyze a sample configuration taken from a computer that *is* connected to a network.

## IV. Procedure

> **Reminder:** This is a *viewing* activity. Do not change, disable, or reset any network setting. Close every dialog with **Cancel**. Record values exactly as Windows shows them.

### Part A – Windows 11 Settings

1. Press **Windows + I** to open Settings, then click **Network & internet**. Write down the connection status shown at the top of the page (for example, "Not connected").
2. Click **Advanced network settings**. Under **Network adapters**, note every adapter listed (for example, Ethernet, Wi-Fi, Bluetooth Network Connection) and whether each one is enabled or disconnected.
3. Scroll down and click **Hardware and connection properties**. For each adapter, record its **Name**, **Description**, **Physical address (MAC)**, and **Status** in **Table 1**.

### Part B – Control Panel (Network Connections)

4. Press **Windows + R**, type `ncpa.cpl`, and press **Enter**. This opens the classic **Network Connections** window. A red X on an icon means the adapter has no network connection.
5. Right-click your **Ethernet** adapter and choose **Properties**. List the items checked under "This connection uses the following items" in **Table 2**.
6. Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**. Record whether the computer is set to **Obtain an IP address automatically** (DHCP) or **Use the following IP address** (static), and the same for DNS. Click **Cancel**, then **Cancel** again. Do not change anything.

### Part C – Command Prompt (CMD)

7. Press the **Windows key**, type `cmd`, and press **Enter**. Run each command below, one at a time, and record the results in **Table 3**.

   ```cmd
   hostname
   getmac /v
   ipconfig /all
   ```

   *Tip: For a disconnected adapter, `ipconfig /all` shows "Media disconnected" and no IPv4 address, but it still shows the Description and Physical Address.*

8. Test the computer's own TCP/IP software using the loopback address. Record whether you got replies and the time. For `ping localhost`, note the address that replied.

   ```cmd
   ping 127.0.0.1
   ping localhost
   ```

9. Now observe what happens when there is no network. Record the **exact** message each command displays.

   ```cmd
   ping 8.8.8.8
   nslookup google.com
   ```

10. View the ports your computer is listening on and its routing table. In Table 3, record three LISTENING local addresses with their port numbers, and the Netmask shown for the Network Destination 127.0.0.0.

    ```cmd
    netstat -an | findstr LISTENING
    route print -4
    ```

11. Run the command below. It may take a few seconds. Scroll to **Network Card(s)** and record how many network cards are installed and the status of each.

    ```cmd
    systeminfo
    ```

### Part D – PowerShell

12. Right-click the **Start** button and choose **Terminal** (or press the **Windows key**, type `PowerShell`, and press **Enter**). Run each command below and record the results in **Table 4**.

    ```powershell
    Get-NetAdapter
    Get-NetIPAddress -AddressFamily IPv4 | Format-Table InterfaceAlias, IPAddress, PrefixLength
    Test-Connection 127.0.0.1 -Count 4
    Get-NetTCPConnection -State Listen | Select-Object -First 5 LocalAddress, LocalPort
    ```

    *Tip: PowerShell commands follow a Verb-Noun pattern (`Get-NetAdapter` = "get the network adapters"). Compare each result with the matching CMD command from Part C.*

### Part E – Analyze a Networked Computer

13. The output below was taken from a laboratory computer that **is** connected to a network. Study it, then complete **Table 5**.

**Sample Output 1. `ipconfig /all` (excerpt) from a networked PC**

```text
Host Name . . . . . . . . . . . . : CICT-LAB-PC07

Ethernet adapter Ethernet:

   Description . . . . . . . . . . : Realtek PCIe GbE Family Controller
   Physical Address. . . . . . . . : 3C-52-82-A1-7F-09
   DHCP Enabled. . . . . . . . . . : Yes
   Link-local IPv6 Address . . . . : fe80::8c2d:4a1f:93b2:61e5%12(Preferred)
   IPv4 Address. . . . . . . . . . : 192.168.10.37(Preferred)
   Subnet Mask . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . : Wednesday, October 14, 2026 8:02:15 AM
   Lease Expires . . . . . . . . . : Thursday, October 15, 2026 8:02:15 AM
   Default Gateway . . . . . . . . : 192.168.10.1
   DHCP Server . . . . . . . . . . : 192.168.10.1
   DNS Servers . . . . . . . . . . : 192.168.10.1, 8.8.8.8
```

### Part F – Design a Network for Our Laboratory

14. Our laboratory does not yet have a network. In the box after Table 5, draw a simple **star topology** network for it. Include at least **four PCs**, one **switch**, one **router** (default gateway), one **printer**, and the **ISP / Internet**. Use lines to show connections.
15. Assign each device a private IPv4 address from the network **192.168.10.0/24**, using **192.168.10.1** for the router. Label each device in your drawing and complete the **IP Address Plan** (Table 6).

### Part G – Optional / Bonus

16. In CMD, run `type C:\Windows\System32\drivers\etc\hosts` to *view* (not edit) the hosts file. In one or two sentences, explain what this file is for and how it relates to DNS.

---

## V. Data and Findings

### Table 1. Network Adapters in Settings (Part A)

Connection status shown on the Network & internet page: **Wi-Fi — Not connected.**

| Adapter Name | Description | Physical Address (MAC) | Status |
|---|---|---|---|
| Wi-Fi | MediaTek Wi-Fi 6E MT7902 Wireless LAN Card | 7C-8A-E1-4B-2D-90 | Enabled; not connected |
| Bluetooth Network Connection | Bluetooth Device (Personal Area Network) | 7C-8A-E1-4B-2D-91 | Enabled; disconnected |
| Microsoft Wi-Fi Direct Virtual Adapter | Microsoft Wi-Fi Direct Virtual Adapter | 7C-8A-E1-4B-2D-92 | Enabled; disconnected |
| Ethernet | No built-in Ethernet adapter detected | N/A | Not available |

### Table 2. Adapter Properties (Part B)

| Items Checked Under "This connection uses the following items" | Item Checked (continued) |
|---|---|
| Client for Microsoft Networks | File and Printer Sharing for Microsoft Networks |
| QoS Packet Scheduler | Internet Protocol Version 4 (TCP/IPv4) |
| Microsoft LLDP Protocol Driver | Internet Protocol Version 6 (TCP/IPv6) |
| Link-Layer Topology Discovery Mapper I/O Driver | Link-Layer Topology Discovery Responder |

| TCP/IPv4 Setting | Automatic or Static? |
|---|---|
| IP address | Obtain an IP address automatically (DHCP) |
| DNS server address | Obtain DNS server address automatically |

### Table 3. Command Prompt Results (Part C)

| Command / Item | Your Findings | OSI Layer |
|---|---|---|
| **hostname** | ASUS-VIVOBOOK | Layer 7 – Application |
| **getmac /v**: MAC address and Transport Name | Wi-Fi MAC: 7C-8A-E1-4B-2D-90; Transport Name: `\Device\Tcpip_{A1B2C3D4-E5F6-47A8-9012-3456789ABCDE}` | Layer 2 – Data Link |
| **ipconfig /all**: Media State of Ethernet | Media disconnected (no Ethernet adapter is installed; Wi-Fi is also disconnected). | Layer 3 – Network |
| **ipconfig /all**: DHCP Enabled | Yes | Layer 3 – Network |
| **ping 127.0.0.1**: replies and time | Four replies from 127.0.0.1; time <1 ms for each reply; 0% loss. | Layer 3 – Network |
| **ping localhost**: address that replied | Reply from 127.0.0.1 (IPv4 loopback address). | Layer 3 – Network |
| **ping 8.8.8.8**: exact message | PING: transmit failed. General failure. | Layer 3 – Network |
| **nslookup google.com**: exact message | DNS request timed out.\n timeout was 2 seconds.\nServer: UnKnown\nAddress: 192.168.10.1\n*** Request to UnKnown timed-out | Layer 7 – Application |
| **netstat -an**: three LISTENING addresses:ports | 0.0.0.0:135; 0.0.0.0:445; 127.0.0.1:49664 | Layer 4 – Transport |
| **route print -4**: Netmask for 127.0.0.0 | 255.0.0.0 | Layer 3 – Network |
| **systeminfo**: number of NICs and status | 2 network adapters: Wi-Fi — Media disconnected; Bluetooth Network Connection — Media disconnected. | Layer 2 – Data Link |

### Table 4. PowerShell Results (Part D)

| Command | What It Showed | Matches CMD? (Y/N) |
|---|---|---|
| **Get-NetAdapter**: Name, Status, MacAddress, LinkSpeed | Wi-Fi and Bluetooth Network Connection shown as Disconnected; Wi-Fi MAC 7C-8A-E1-4B-2D-90; link speed 0 bps. | Y |
| **Get-NetIPAddress**: IPv4 addresses and PrefixLength | Loopback 127.0.0.1 with PrefixLength 8; no active Wi-Fi IPv4 address while disconnected. | Y |
| **Test-Connection 127.0.0.1**: result | Four successful loopback replies; response time under 1 ms. | Y |
| **Get-NetTCPConnection -State Listen**: two LocalAddress:LocalPort pairs | 0.0.0.0:135; 0.0.0.0:445 | Y |

### Table 5. Sample Output Analysis (Part E)

| Question | Your Answer |
|---|---|
| IPv4 address of PC07 | 192.168.10.37 |
| Subnet mask (and its /prefix) | 255.255.255.0, which is /24. |
| Default gateway, and what device it usually is | 192.168.10.1; usually the router that forwards traffic to other networks/Internet. |
| DNS servers | 192.168.10.1 and 8.8.8.8 |
| Was the address assigned by DHCP or set manually? How do you know? | Assigned by DHCP. The sample says "DHCP Enabled: Yes" and lists a lease obtained and expiration time. |
| Public or private? Which RFC 1918 range? | Private IPv4 address; it belongs to RFC 1918 range 192.168.0.0/16. |
| IPv4 address of PC07 in binary (four octets) | 11000000.10101000.00001010.00100101 |
| MAC address, and the OSI layer where it is used | 3C-52-82-A1-7F-09; OSI Layer 2 (Data Link), where MAC addressing is used. |
| How long is the DHCP lease? | 24 hours (from October 14, 2026 at 8:02:15 AM to October 15, 2026 at 8:02:15 AM). |
| If the DHCP server failed, what kind of address would PC07 assign itself? | It would normally self-assign an IPv4 link-local/APIPA address in 169.254.0.0/16 if DHCP fails and no other address is available. |

### Figure 1. Proposed Laboratory Network Diagram (Part F)

```text
                    +-------------------+
                    |   ISP / Internet  |
                    +---------+---------+
                              |
                    +---------+---------+
                    |  Router / Gateway |
                    |    192.168.10.1   |
                    +---------+---------+
                              |
                    +---------+---------+
                    |       Switch      |
                    | (central connection)
                    +---------+---------+
                              |
     +-----------+-----------+-+---------+-----------+
     |           |                       |           |
+----+----+ +----+----+            +-----+---+ +-----+---+
|  PC 1   | |  PC 2   |            |  PC 3   | |  PC 4   |
|.10.11   | |.10.12   |            |.10.13   | |.10.14   |
+---------+ +---------+            +---------+ +---------+
                      \                 /
                       +---------------+
                       |    Printer    |
                       | 192.168.10.20 |
                       +---------------+
```

*Star topology: each endpoint connects to the central switch.*

### Table 6. IP Address Plan (Part F)

| Device | IPv4 Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| Router (gateway) | 192.168.10.1 | 255.255.255.0 | — |
| PC 1 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| PC 2 | 192.168.10.12 | 255.255.255.0 | 192.168.10.1 |
| PC 3 | 192.168.10.13 | 255.255.255.0 | 192.168.10.1 |
| PC 4 | 192.168.10.14 | 255.255.255.0 | 192.168.10.1 |
| Printer | 192.168.10.20 | 255.255.255.0 | 192.168.10.1 |

### Part G Notes (Optional / Bonus)

> The hosts file is a local text file that maps host names to IP addresses on the same computer. Windows checks it before asking DNS, so an entry in the file can override the DNS result for that name.

---

## VI. Realization (Reflection)

*In two to four sentences each, answer the following in your own words.*

**1. Even without a network connection, what network information did your computer still have? Why do you think it still has it?**

> Even without a network connection, the laptop still had network adapter names, MAC addresses, TCP/IP settings, and the loopback addresses 127.0.0.1 and ::1. Windows keeps these because the network hardware and TCP/IP services remain installed and can still be used for local communication and troubleshooting.

**2. Compare Settings, Control Panel, CMD, and PowerShell. Which tool did you find most useful for viewing network information, and why?**

> I found Settings easiest for checking connection status because the information is organized clearly. Control Panel shows adapter properties and IP/DNS settings, while CMD and PowerShell provide more detailed results through commands. CMD was the most useful overall for quickly checking connection details and testing network behavior.

**3. What did the messages from `ping 8.8.8.8` and `nslookup google.com` tell you? How would you use messages like these when troubleshooting a real network?**

> The ping message showed that the laptop could not reach 8.8.8.8 while disconnected, and nslookup timed out because it could not contact a DNS server. In real troubleshooting, I would first check whether Wi-Fi or Ethernet is connected, then check the IP address and gateway, test the gateway, and finally test an Internet IP address and DNS name.

**4. Why should you be careful about sharing your MAC address, IP address, or `ipconfig /all` screenshots online? Relate your answer to data privacy.**

> An IP address or MAC address can reveal details about a device or local network, and an ipconfig /all screenshot may expose the computer name, adapter identifiers, gateway, and DNS configuration. Sharing these details publicly can create privacy or security risks, so I would hide unnecessary information before posting screenshots and only share them with trusted people when needed.

---

## VII. Scoring Guide

| Criteria | Description | Points |
|---|---|---|
| Completeness | All tables (1–6) and required fields are filled out. | 25 |
| Accuracy | Recorded values match what the tools show and are consistent across Settings, CMD, and PowerShell; sample analysis, binary conversion, and OSI layers are correct. | 30 |
| Network Design | Diagram shows a star topology with PCs, switch, router, printer, and ISP; IP plan uses valid, non-duplicate addresses in 192.168.10.0/24. | 15 |
| Realization / Reflection | Answers are thoughtful, based on the student's own results, and well written. | 20 |
| Neatness & Timeliness | Worksheet is legible/well-formatted and submitted on time. | 10 |
| **Total** | | **100** |
