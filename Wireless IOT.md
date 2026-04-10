# Building a Wireless and IoT Network in Packet Tracer (NETLAB+)

**Course:** CTS1133C – Software Configuration  
**Module:** 10, Labs – Part 3  
**Environment:** Cisco Packet Tracer (Standalone)  
**Objective:** Build a wireless network with a WRT300N router, laptop, tablet, and smartphone. Then extend the network with a wired segment containing a switch, PC, server, and IoT devices (solar panel, power meter, battery, appliance, and lamp) managed through an IoT registration server.

---

## Prerequisites

- Cisco Packet Tracer installed on your computer
- Completed Module 8 Lab (familiarity with Packet Tracer interface, device placement, and cabling)

---

## PART 1: Build a Wireless Network

### Step 1 – Open Packet Tracer

1. Open **Cisco Packet Tracer** and log in or use **Guest Login**.

### Step 2 – Place the wireless router

3. In the bottom-left device panel, select **Network Devices** (top row, first icon).
4. On the bottom row, select the **Wireless Devices** icon — it looks like it has wireless waves emitting outward.
5. From the models that appear to the right, select the **WRT300N** wireless router and drag it into the workspace.

> **📝 Note – What is the WRT300N?**  
> The Linksys WRT300N is a **consumer-grade wireless router** that combines three functions in one device:
> 1. **Wireless Access Point (AP):** Creates a Wi-Fi network that wireless devices can join using an SSID.
> 2. **Router:** Routes traffic between the wireless LAN and a wired WAN or LAN segment.
> 3. **DHCP Server:** Automatically assigns IP addresses to devices that connect to the network.
>
> By default, the WRT300N assigns itself **192.168.0.1** with a subnet mask of **255.255.255.0** and starts handing out addresses from **192.168.0.100** onward. This means the network is **192.168.0.0/24**, where:
> - **Network portion:** 192.168.0 (the first three octets, determined by the /24 or 255.255.255.0 mask)
> - **Host portion:** The last octet (0–255), giving 254 usable addresses (192.168.0.1 through 192.168.0.254)
> - The router itself uses .1, and DHCP clients receive addresses starting at .100

### Step 3 – Place end devices

6. Select **End Devices** from the top row (second icon from the left).
7. Drag a **Laptop** (second icon from the left) into the workspace below the wireless router.
8. Drag a **Tablet** into the workspace (you may need to scroll the models list).
9. Drag a **Smartphone** (Smart) into the workspace.

> **📸 Screenshot Suggestion:** Capture the workspace with all four devices placed. The tablet and smartphone should already show wireless signal lines to the router (they have built-in wireless adapters), but the laptop will not yet — it needs a wireless adapter installed.

### Step 4 – Install a wireless adapter in the laptop

The generic laptop comes with a **wired RJ-45 network adapter** by default. You need to replace it with a wireless adapter.

10. Click on the **Laptop** icon in the workspace to open its properties.
11. On the **Physical** tab, **zoom in** to see the laptop's ports. Note the power button and the RJ-45 adapter on the side.
12. Click the **power button** once to power off the laptop. The power light goes off.
13. Click and drag the **RJ-45 adapter** out of the laptop and drop it in the bottom-right area of the window. The expansion slot is now empty.
14. From the **MODULES** list on the left, click **PT-LAPTOP-NM-1W** (a wireless interface module).
15. Drag the **NM-1W adapter** from the bottom-right area into the empty expansion slot on the laptop.
16. Click the **power button** again to turn the laptop back on.

> **📝 Note – Why swap the adapter?**  
> In real-world scenarios, laptops typically include both wired (Ethernet) and wireless (Wi-Fi) adapters. In Packet Tracer, the generic laptop only has one expansion slot, so you must choose. Since this lab focuses on wireless networking, we replace the wired NIC with the **PT-LAPTOP-NM-1W**, which provides a 2.4GHz 802.11 wireless interface. This mirrors physically installing a wireless card into a laptop's Mini PCIe slot. The laptop must be powered off before swapping hardware — just like real hardware installation.

> **📸 Screenshot Suggestion:** Capture the laptop's Physical tab showing the wireless adapter successfully installed in the expansion slot.

### Step 5 – Configure the wireless router SSID

17. Click the **WRT300N** wireless router in the workspace.
18. Select the **Config** tab → **Wireless** from the left menu.
19. In the **SSID** field, change the value from "Default" to a custom name (e.g., `Andrine-WiFi`).

> **📝 Note – What is an SSID?**  
> The **Service Set Identifier (SSID)** is the human-readable name of a wireless network. When you scan for Wi-Fi on your phone or laptop, the names you see are SSIDs. Changing it from "Default" to something unique serves two purposes:
> 1. **Identification:** On a skills test with multiple students, a unique SSID ensures your devices connect to *your* router, not someone else's.
> 2. **Security (minimal):** While hiding or renaming an SSID is not true security, using a default SSID signals to attackers that the device may still have default credentials.

### Step 6 – Explore the GUI tab settings

20. Select the **GUI** tab on the wireless router.
21. Scroll through the **Setup** page and observe:
    - The router IP address: **192.168.0.1**
    - Subnet mask: **255.255.255.0**
    - DHCP Server: **Enabled**
    - Start IP Address: **192.168.0.100**
22. Navigate to **Wireless > Basic Wireless Settings** — note the SSID broadcast setting.
23. Scroll to the bottom and click **Save Settings**.
24. Close the wireless router window.

> **📝 Note – Understanding the IP addressing scheme:**  
>
> | Setting | Value | Meaning |
> |---|---|---|
> | Router IP | 192.168.0.1 | The router's address on the LAN (also the default gateway for all clients) |
> | Subnet mask | 255.255.255.0 | /24 network — first 24 bits are the network portion |
> | DHCP range start | 192.168.0.100 | First address the router will automatically assign |
> | Network address | 192.168.0.0 | Identifies the entire subnet (not assignable to a device) |
> | Broadcast address | 192.168.0.255 | Sends to all hosts on the subnet (not assignable) |
>
> **Identifying the network vs. host portions:**  
> With a 255.255.255.0 mask, the IP address 192.168.0.103 breaks down as:
> - **Network portion:** `192.168.0` — all devices on this network share these three octets
> - **Host portion:** `.103` — unique to this specific device
>
> Any device with an IP in the range 192.168.0.1–192.168.0.254 and a mask of 255.255.255.0 is on the **same subnet** and can communicate directly without routing.

### Step 7 – Connect the laptop to the wireless network

25. Click the **Laptop** icon in the workspace.
26. Select the **Config** tab → **Wireless0** from the left menu.
27. In the **SSID** field, type the **same SSID** you configured on the wireless router (e.g., `Andrine-WiFi`).

A **wireless signal indicator** (animated dashes) should appear between the laptop and the wireless router in the workspace.

> **📝 Note – SSID matching:**  
> For a wireless client to associate with an access point, the **SSID must match exactly** (case-sensitive). This is the equivalent of plugging an Ethernet cable into a switch port — it establishes the Layer 2 connection. Once associated, the laptop will request an IP address via DHCP automatically.

### Step 8 – Connect the tablet and smartphone

28. Click the **Tablet PC** icon → **Config** tab → **Wireless0** → enter the same SSID.
29. Click the **Smartphone** icon → **Config** tab → **Wireless0** → enter the same SSID.

When all devices are connected, you should see wireless signal lines between **all three wireless devices** and the WRT300N.

> **📸 Screenshot Suggestion:** Capture the full wireless network showing all three devices connected to the WRT300N with wireless signal indicators visible. *This is a required submission screenshot.*

### Step 9 – Verify IP addressing

30. Click the **Laptop** icon → **Desktop** tab → **IP Configuration**.
31. Verify the laptop received an IP address starting with **192.168.0.1xx**, a subnet mask of **255.255.255.0**, and a default gateway of **192.168.0.1**.
32. Check the tablet and smartphone similarly (tablet via **Config** tab, smartphone via **Config** tab).

> **📝 Note – DHCP in action:**  
> Each device sends a DHCP Discover broadcast when it joins the wireless network. The WRT300N's built-in DHCP server responds with an IP address from its pool (starting at 192.168.0.100). The assigned addresses might be .100, .101, .102, etc., depending on the order devices connected. If a device doesn't receive an address, try toggling its IP Configuration from Static to DHCP, or verify the SSID matches exactly.

> **Troubleshooting:** If any device shows 0.0.0.0 or no IP address:
> 1. Verify the SSID matches exactly on both the router and the device.
> 2. Toggle the IP Configuration radio button from DHCP → Static → DHCP.
> 3. Check that the wireless signal indicator is visible between the device and the router.

---

## PART 2: Connect Wired and IoT Devices to the Network

### Step 10 – Place the switch, PC, and server

33. Select **Network Devices** → **Switches** (bottom row, second icon). Drag a **2960** switch into the workspace to the right of the wireless router.
34. Select **End Devices**. Drag a **PC** above the switch. Drag a **Server** above the switch to the right of the PC.

> **📝 Note – Why add a switch and wired devices?**  
> The WRT300N has four built-in Ethernet LAN ports, but in a real-world deployment you'd use a **dedicated switch** to extend the wired network. The switch provides additional ports and operates at Layer 2, forwarding frames to the correct port based on MAC addresses. The server will run an **IoT registration service** — a central management point for monitoring IoT devices. This hybrid topology (wireless + wired) reflects modern networks where wireless clients coexist with wired servers and infrastructure.

### Step 11 – Cable the wired devices

35. Using the **Connections** tool (lightning bolt icon), select **Copper Straight-Through** cable and make the following connections:

| From Device | From Port | To Device | To Port |
|---|---|---|---|
| Wireless Router0 | Ethernet 1 | Switch0 | FastEthernet0/1 |
| PC0 | FastEthernet0 | Switch0 | FastEthernet0/2 |
| Server0 | FastEthernet0 | Switch0 | FastEthernet0/3 |

> **📝 Note – Connecting the wireless router to the switch:**  
> The WRT300N's **Ethernet 1** port is one of its four LAN ports. By connecting it to the switch, we extend the same **192.168.0.0/24** network to the wired segment. The switch doesn't perform any routing — it simply bridges frames between its ports. This means the PC and server on the switch will receive DHCP addresses from the same pool as the wireless devices, and all devices (wired and wireless) can communicate directly because they're on the same subnet.

> **📸 Screenshot Suggestion:** Capture the topology showing both the wireless network and the wired segment with the switch, PC, and server cabled.

### Step 12 – Configure the server

36. Click **Server0** → **Services** tab → **IoT** → select the **On** radio button.
37. Go to **Desktop** tab → **IP Configuration** and assign a **static IP**:
    - IP Address: **192.168.0.2**
    - Subnet Mask: **255.255.255.0**
    - Default Gateway: **192.168.0.1**

> **📝 Note – Why a static IP for the server?**  
> We assign the server a **static** (manually configured) IP address of **192.168.0.2** instead of using DHCP because:
> 1. **Predictability:** IoT devices need to know the server's address to register with it. If the server's IP changed every time it rebooted (as DHCP addresses can), the IoT devices would lose their connection.
> 2. **Convention:** Servers, routers, and other infrastructure devices are typically given **low, static addresses** in the subnet. The router is .1, the server is .2, and DHCP clients get addresses from .100 and up — keeping the ranges cleanly separated.
>
> The address **192.168.0.2** breaks down the same way:
> - **Network:** 192.168.0 (matches all other devices on this subnet)
> - **Host:** .2 (unique identifier for this server)

### Step 13 – Configure the PC

38. Click **PC0** → **Desktop** tab → **IP Configuration** → select **DHCP**.
39. The PC should receive an IP like **192.168.0.10x**, subnet mask **255.255.255.0**, and gateway **192.168.0.1**.

### Step 14 – Set up the IoT registration server account

40. On **PC0**, go to **Desktop** tab → **Web Browser**.
41. In the URL bar, type **192.168.0.2** and press Enter. The Registration Server Login page appears.
42. Click **Sign up now** at the bottom.
43. Enter Username: **admin**, Password: **admin**, then click **Create**.

> **📸 Screenshot Suggestion:** Capture the Registration Server Login screen from the PC's web browser.

### Step 15 – Place IoT devices

44. Close all device windows. From the main Packet Tracer window:
45. Select **End Devices** (top row) → **Power Grid** (bottom row, last icon — looks like a power grid tower).
46. Drag a **Solar Panel** above the router.
47. Drag a **Power Meter** (third icon from the left) to the right of the solar panel.
48. Drag a **Battery** (first icon — green battery) below the solar panel and power meter.
49. Select the **Home** icon from the bottom row (looks like a house).
50. Drag an **Appliance** (looks like a coffee pot) to the right of the battery.
51. Drag a **Light** (lamp with lampshade) above the appliance.

### Step 16 – Connect IoT devices to the wireless network

52. Click the **Solar Panel** icon → **Config** tab → **Wireless0** → enter the same SSID used throughout (e.g., `Andrine-WiFi`).
53. Repeat for the **Battery** and the **Power Meter** — each gets the same SSID.

Wireless signal indicators should appear between each IoT device and the WRT300N.

> **📝 Note – IoT devices on Wi-Fi:**  
> The solar panel, power meter, and battery each have a built-in wireless interface. By joining the same SSID and subnet (192.168.0.0/24), they become reachable from the server and PC. This models real-world IoT deployments where sensors and controllers connect via Wi-Fi to a central management platform. The appliance and lamp do *not* connect to Wi-Fi — they receive power from the battery through custom IoT cables.

> **📸 Screenshot Suggestion:** Capture the topology showing all IoT devices connected wirelessly to the router.

### Step 17 – Cable IoT devices together with IoT Custom Cable

54. Select the **Connections** tool (lightning bolt) → choose the **IoT Custom Cable**.
55. Make the following connections:

| From Device | From Port | To Device | To Port |
|---|---|---|---|
| Solar Panel (IoT0) | D0 | Power Meter (IoT1) | D0 |
| Power Meter (IoT1) | D1 | Battery (IoT2) | D0 |
| Battery (IoT2) | D1 | Appliance (IoT3) | D0 |
| Battery (IoT2) | D2 | Lamp (IoT4) | D0 |

> **📝 Note – IoT Custom Cable and the Dx ports:**  
> The **IoT Custom Cable** is unique to Packet Tracer and simulates the proprietary or specialized connections between IoT components. The **Dx ports** (D0, D1, D2) represent digital I/O connections. The wiring chain here models a real-world off-grid power system:
> - The **solar panel** generates power and feeds it to the **power meter** (D0 → D0).
> - The power meter passes energy to the **battery** for storage (D1 → D0).
> - The battery distributes stored power to the **appliance** (D1 → D0) and **lamp** (D2 → D0).

> **📸 Screenshot Suggestion:** Capture the full topology showing all IoT devices with both wireless connections and IoT custom cables visible.

### Step 18 – Register IoT devices with the server

56. Click the **Solar Panel** icon → **Config** tab → **Wireless0** → in the IP Configuration section, select **DHCP**. Confirm it receives a 192.168.0.x address.
57. Still on the solar panel, select **Settings** from the left menu. Scroll to the **IoT Server** section:
    - Select **Remote Server**
    - Server Address: **192.168.0.2**
    - User Name: **admin**
    - Password: **admin**
    - Click **Connect** (or Refresh)
58. Repeat steps 56–57 for the **Power Meter** and **Battery**.

> **📝 Note – IoT device IP assignment:**  
> The solar panel, power meter, and battery each get DHCP addresses from the WRT300N (e.g., .104, .105, .106). Each device then registers with the IoT server at 192.168.0.2 using the admin credentials you created earlier. This is conceptually similar to how real IoT platforms (like AWS IoT Core or Azure IoT Hub) work — devices authenticate to a central server and report telemetry data.

### Step 19 – Verify IoT registration

59. On **PC0**, open the **Web Browser** (Desktop tab).
60. Navigate to **192.168.0.2**.
61. Log in with Username: **admin**, Password: **admin**.
62. Click **Sign In**. You should see **three IoT devices** listed (solar panel, power meter, battery).

> **📸 Screenshot Suggestion:** Capture the IoT registration server's home page showing three registered devices. *This is the final deliverable screenshot for this lab.*

> **Troubleshooting – Battery charge issues:**  
> If the battery loses all charge and the solar panel's wattage doesn't increase after a few minutes, delete the IoT Custom Cable connections between the solar panel, power meter, and battery Dx ports, then reconnect them. This forces Packet Tracer to reset the power simulation.

---

## Summary

This lab built a hybrid network with three distinct segments all on the **192.168.0.0/24** subnet:

| Segment | Devices | Connection Type |
|---|---|---|
| Wireless LAN | Laptop, Tablet, Smartphone | Wi-Fi (802.11) via WRT300N |
| Wired LAN | PC0, Server0 | Copper straight-through via 2960 switch |
| IoT (Wireless + Custom) | Solar Panel, Power Meter, Battery | Wi-Fi to router + IoT Custom Cables between devices |
| IoT (Power only) | Appliance, Lamp | IoT Custom Cable from battery (no network connection) |

### IP Address Map

| Device | IP Address | Assignment Method | Role |
|---|---|---|---|
| WRT300N | 192.168.0.1 | Static (factory default) | Router / AP / DHCP Server |
| Server0 | 192.168.0.2 | Static (manually configured) | IoT Registration Server |
| PC0 | 192.168.0.10x | DHCP | Management workstation |
| Laptop | 192.168.0.10x | DHCP | Wireless client |
| Tablet | 192.168.0.10x | DHCP | Wireless client |
| Smartphone | 192.168.0.10x | DHCP | Wireless client |
| Solar Panel | 192.168.0.10x | DHCP | IoT sensor |
| Power Meter | 192.168.0.10x | DHCP | IoT sensor |
| Battery | 192.168.0.10x | DHCP | IoT sensor/actuator |

> All devices share the subnet mask **255.255.255.0** and use **192.168.0.1** as their default gateway.

---

## Key Networking Concepts Reinforced

| Concept | How It Applied |
|---|---|
| **SSID** | All wireless devices must match the router's SSID to associate |
| **DHCP** | WRT300N auto-assigned IPs from its pool starting at .100 |
| **Static IP** | Server assigned .2 manually for predictable reachability |
| **Default gateway** | All devices use 192.168.0.1 (the router) as their exit point |
| **Subnet mask /24** | 255.255.255.0 — network portion is first 3 octets, host is the 4th |
| **Layer 2 switch** | Extended the wired network without creating a new subnet |
| **IoT management** | Central server model for registering and monitoring IoT devices |
| **Hybrid topology** | Wireless and wired segments coexisting on the same subnet |
