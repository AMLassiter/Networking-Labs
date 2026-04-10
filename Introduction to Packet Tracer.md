# Introduction to Packet Tracer (NETLAB+)

**Course:** CTS1133C – Software Configuration  
**Module:** 8, Lab 7 – Part 1  
**Environment:** Cisco Packet Tracer (Standalone)  
**Objective:** Build a small wired network topology using a router, two switches, PCs, and printers. Learn the Packet Tracer interface, device placement, and cabling fundamentals.

---

## Prerequisites

- Cisco Packet Tracer installed on your computer (free with a Cisco Networking Academy account)

---

## Part 1: Launch Packet Tracer and Explore the Interface

### Step 1 – Log in to NETLAB+ and open Packet Tracer

1. Open **Cisco Packet Tracer** on your computer. Log in with your Cisco Networking Academy credentials or select **Guest Login** (available after a few seconds).
2. The application opens to a blank workspace.

> **📸 Screenshot Suggestion:** Capture the Packet Tracer window in its default state showing the blank workspace, toolbar, and device selection panel in the bottom-left corner.

![image alt](https://github.com/AMLassiter/Networking-Labs/blob/db0843db177708923f97fd05e3c2209bff2b73a9/IPT%20Step%201.png)
> 

### Step 2 – Identify the Select tool

4. In the **top-left toolbar**, locate the default **Select tool** — it looks like a dotted rectangle with an arrow in the corner.
5. Hover your cursor over it and confirm the tooltip reads **"Select (Esc)"**.

> **📝 Note – Why the Select tool matters:**  
> The Select tool is the default interaction mode in Packet Tracer. It allows you to click on devices to open their configuration windows, drag devices around the workspace, and interact with device properties. You'll use it constantly — any time you're not actively cabling, you should be in Select mode. Pressing `Esc` returns you to this tool from any other mode.

### Step 3 – Explore the device selection panel

6. Look at the **bottom-left corner** of the screen. This is the **device selection panel** organized in two rows:
   - **Top row:** Device categories (Network Devices, End Devices, etc.)
   - **Bottom row:** Subcategories and specific models for the selected category

7. Click the **first icon in the top row** (Network Devices — looks like a circle with a square and rectangle). Notice routers appear in the bottom row, and specific router models appear in the right-side frame.

> **📝 Note – Understanding the device hierarchy:**  
> Packet Tracer organizes devices in a three-level hierarchy: **Category → Subcategory → Model**. When you select "Network Devices" (top row), you see device types like routers, switches, and hubs (bottom row). Selecting a type then reveals specific hardware models in the frame to the right. This mirrors real-world network procurement — you first decide *what kind* of device you need, then choose a *specific model*.

---

## Part 2: Build the Network Topology

### Step 4 – Place the router

8. With **Network Devices** selected in the top row, ensure **Routers** are selected in the bottom row (first icon on the left).
9. In the models frame to the right, scroll until you find the **1841** router model.
10. **Click and drag** the 1841 router into the center of the workspace. It appears labeled **Router0**.

> **📝 Note – Why the 1841 router?**  
> The Cisco 1841 is an Integrated Services Router (ISR) commonly used in small-to-medium networks. In this lab, it serves as the **central device connecting two separate network segments** (one on each side). Routers operate at **Layer 3 (Network Layer)** of the OSI model — they make forwarding decisions based on IP addresses. Unlike switches, routers can connect *different* networks and route traffic between them. Each router interface (e.g., FastEthernet0/0 and FastEthernet0/1) connects to a separate network segment, creating distinct broadcast domains.

> **📸 Screenshot Suggestion:** Capture the workspace showing Router0 placed in the center.
>
![image alt](https://github.com/AMLassiter/Networking-Labs/blob/ba9284a4e822ff7c68cef76a5fdc3965d54dc1cb/IPT%20Step%2010.png)

### Step 5 – Place the switches

11. In the bottom-left corner bottom row, select the **Switch** icon (immediately to the right of the router icon).
12. Select the **2960** switch model (first one on the left) and drag it into the workspace **to the left** of Router0. It appears as **Switch0**.
13. Drag another **2960** switch and place it **to the right** of Router0. It appears as **Switch1**.

> **📝 Note – Why the 2960 switch? Why two of them?**  
> The Cisco Catalyst 2960 is a managed Layer 2 switch with 24 FastEthernet ports and 2 GigabitEthernet uplinks. Switches operate at **Layer 2 (Data Link Layer)** and forward frames based on **MAC addresses**. They create a single broadcast domain for all connected devices.
>
> We use **two switches** to simulate two separate departments or areas within an organization. Each switch serves as a central connection point for its group of end devices (PCs and printers). The router sits between them to route traffic from one network segment to the other. This is a classic **router-on-a-stick** or **inter-VLAN routing** foundation topology.

> **📸 Screenshot Suggestion:** Capture the workspace showing Switch0, Router0, and Switch1 arranged left to right.
>
![image alt](https://github.com/AMLassiter/Networking-Labs/blob/ac226c3fd379138e81eb9a8bf065e2372bf6c651/IPT%20Step%2013.png)

### Step 6 – Place end devices (PCs and printers)

14. From the top row of the device panel, select the **End Devices** icon (second icon from the left).
15. Ensure **End Devices** is also selected on the bottom row.
16. Drag **two PCs** (first icon from the left) and place them **below Switch0**.
17. Drag **two more PCs** and place them **below Switch1**.
18. Drag a **generic Printer** icon and place it below Switch0 (alongside the PCs).
19. Drag another **generic Printer** and place it below Switch1.

Your topology should now show:
- Switch0 (left) with PC0, PC1, and Printer0 beneath it
- Router0 (center)
- Switch1 (right) with PC2, PC3, and Printer1 beneath it

> **📝 Note – End devices and their role:**  
> PCs and printers are **end devices** (also called hosts). They generate and consume network traffic. In a real network, these would be workstations, servers, printers, IP phones, etc. Each end device has at least one **network interface** (typically FastEthernet0) that connects to a switch port. End devices need an **IP address**, **subnet mask**, and **default gateway** to communicate across network segments — but in this introductory lab, we're only building the physical topology. IP addressing comes in a later module.

> **📸 Screenshot Suggestion:** Capture the full topology with all devices placed (before cabling).
>
![image alt](https://github.com/AMLassiter/Networking-Labs/blob/47aa0a57a5c812b6f2ee2e5cfbfa3e9966c367ca/IPT%20Step%2019.png)

---

## Part 3: Cable the Network

### Step 7 – Select the cabling tool

20. From the bottom-left corner, select the **Connections** icon — it looks like a **lightning bolt**.
21. In the cable selection frame, select the **Copper Straight-Through** cable (solid black line, third from the left).

> **📝 Note – Cable types in Packet Tracer:**  
> - **Straight-through cable** (solid black line): Connects *unlike* devices — a PC to a switch, a switch to a router, a printer to a switch. This is the most common cable type.
> - **Crossover cable** (dashed line): Connects *like* devices — switch to switch, PC to PC, router to router.
> - **Console cable** (light blue): Used for out-of-band management access to a device's CLI.
>
> In this lab, every connection is between an unlike pair (end device ↔ switch, or switch ↔ router), so we use **straight-through** cables exclusively.

### Step 8 – Cable end devices to Switch0 (left side)

22. With the straight-through cable selected, click on **PC1**. A port menu appears — select **FastEthernet0**.
23. Move your cursor to **Switch0** and click on it. Select **FastEthernet0/1**. A cable appears between the two devices.
24. Repeat this process for the remaining left-side devices:

| From Device | From Port | To Device | To Port |
|---|---|---|---|
| PC0 | FastEthernet0 | Switch0 | FastEthernet0/2 |
| PC1 | FastEthernet0 | Switch0 | FastEthernet0/1 |
| Printer0 | FastEthernet0 | Switch0 | FastEthernet0/3 |

> **📝 Note – Port numbering conventions:**  
> Switch ports are numbered as **FastEthernet0/X** where 0 is the module number and X is the port number. The 2960 switch has ports FastEthernet0/1 through FastEthernet0/24 plus two GigabitEthernet uplinks. End devices typically have a single **FastEthernet0** port. Which specific switch port you assign to each device doesn't functionally matter at this stage, but consistent documentation makes troubleshooting easier. In production environments, port assignments are tracked in a **port map** or **network documentation**.

### Step 9 – Cable end devices to Switch1 (right side)

25. Cable the right-side devices the same way:

| From Device | From Port | To Device | To Port |
|---|---|---|---|
| PC2 | FastEthernet0 | Switch1 | FastEthernet0/1 |
| PC3 | FastEthernet0 | Switch1 | FastEthernet0/2 |
| Printer1 | FastEthernet0 | Switch1 | FastEthernet0/3 |

> **📸 Screenshot Suggestion:** Capture the topology showing all end devices cabled to their respective switches (before router cabling). The cable endpoint dots will be green on the switch side (ports auto-enable) and green on the end device side.

### Step 10 – Cable switches to the router

26. Using the same straight-through cable, connect the switches to the router:

| From Device | From Port | To Device | To Port |
|---|---|---|---|
| Router0 | FastEthernet0/0 | Switch0 | FastEthernet0/24 |
| Router0 | FastEthernet0/1 | Switch1 | FastEthernet0/24 |

> **📝 Note – Why the cable endpoints are red on the router side:**  
> Unlike switches (whose ports are enabled by default), **router interfaces are administratively shut down by default**. This is a Cisco security best practice — router ports should only be active when intentionally configured. The red dots on the router end of the cables indicate the interface is down. We will enable them in the next step. The switch-side dots may be orange initially (STP convergence) before turning green.

> **📝 Note – Port selection strategy:**  
> We use **FastEthernet0/24** on each switch for the uplink to the router. This is a convention — many network administrators reserve the higher-numbered ports for uplinks (connections to routers or other switches) and use lower-numbered ports for end devices. The router has two FastEthernet interfaces: **FastEthernet0/0** connects to the left network segment (Switch0), and **FastEthernet0/1** connects to the right segment (Switch1). Each router interface will eventually be assigned an IP address from a *different* subnet, enabling it to route traffic between the two networks.

---

## Part 4: Enable Router Interfaces

### Step 11 – Bring the router ports up

27. Click on the **Router0** icon in the workspace to open its configuration window.
28. Select the **Config** tab.
29. From the left menu, select **FastEthernet0/0**.
30. Check the **Port Status → On** checkbox. A status message appears: *"Interface FastEthernet0/0 changed state to up."*
31. From the left menu, select **FastEthernet0/1**.
32. Check the **Port Status → On** checkbox. You'll see the same up-state message.
33. Close the Router0 window.

> **📝 Note – Interface states:**  
> Cisco router interfaces have two status indicators:
> - **Administrative status:** Whether the interface is enabled (`no shutdown`) or disabled (`shutdown`). We just changed this from down to up.
> - **Line protocol status:** Whether the interface detects a valid connection on the other end. With the cables connected and the switch ports active, line protocol should come up automatically.
>
> After enabling both router interfaces, the red cable dots turn **orange** briefly (while STP converges on the switch side), then **green** — indicating full Layer 1/Layer 2 connectivity.

> **📸 Screenshot Suggestion:** Capture the **completed topology with all cable indicators showing green**. This is the final deliverable screenshot for this lab.

---

## Summary

In this lab, you built a foundational wired network topology consisting of:

- **1 Router (1841):** Central device connecting two network segments via FastEthernet0/0 and FastEthernet0/1
- **2 Switches (2960):** Each providing a local connection point for end devices in its segment
- **4 PCs and 2 Printers:** End devices split across the two segments
- **Copper straight-through cables:** Connecting unlike devices throughout the topology

**What this topology does not yet have:** IP addressing, subnet masks, or default gateways. The physical connectivity is complete, but no data can be routed until Layer 3 configuration is applied in a future lab.

---

## Key Networking Concepts Reinforced

| Concept | How It Applied |
|---|---|
| **OSI Layer 1 (Physical)** | Cabling devices, port types, enabling interfaces |
| **OSI Layer 2 (Data Link)** | Switches forwarding based on MAC addresses |
| **OSI Layer 3 (Network)** | Router placed between segments (IP config in future lab) |
| **Straight-through vs. crossover** | All connections were between unlike devices |
| **Router interfaces default to shutdown** | Had to manually enable FastEthernet0/0 and 0/1 |
| **Port numbering** | FastEthernet0/X on switches; FastEthernet0/X on router |
