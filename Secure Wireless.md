# Build a Secure Wireless Network in Packet Tracer (NETLAB+)

**Course:** CTS1133C – Software Configuration  
**Module:** 11, Labs – Part 2  
**Environment:** Cisco Packet Tracer (Standalone)  
**Objective:** Build a wireless network using a WRT300N wireless router, a laptop with a WPC300N wireless adapter, and a wireless tablet. Apply wireless security (WEP, WPA Personal, or WPA2 Personal) and verify connectivity with ping tests.

---

## Prerequisites

- Cisco Packet Tracer installed on your computer
- Completed Module 10, Part 3 Lab (familiarity with wireless network construction, SSID configuration, and adapter installation)

---

## Part 1: Build the Wireless Network

### Step 1 – Open Packet Tracer

1. Open **Cisco Packet Tracer** and log in or use **Guest Login** (available after a few seconds).

### Step 2 – Place the wireless router

3. Select **Network Devices** (bottom-left panel, top row, first icon) → **Wireless Devices** (bottom row).
4. Drag the **WRT300N** wireless router into the workspace.

### Step 3 – Place the laptop and tablet

5. Select **End Devices** (top row, second icon).
6. Drag a **Generic Laptop** into the workspace below the router.
7. Drag a **Wireless Tablet** into the workspace.

### Step 4 – Install the wireless adapter in the laptop

The generic laptop has a wired RJ-45 adapter by default. Replace it with the **WPC300N** wireless adapter:

8. Click the **Laptop** icon → **Physical** tab.
9. Click the **power button** to turn the laptop off.
10. Drag the **RJ-45 adapter** out of the laptop's expansion slot (drop it in the bottom-right corner).
11. From the **MODULES** list on the left, select **WPC300N**.
12. Drag the **WPC300N** adapter into the empty expansion slot.
13. Click the **power button** to turn the laptop back on.

> **📝 Note – WPC300N vs. PT-LAPTOP-NM-1W:**  
> In the Module 10 lab, you installed the PT-LAPTOP-NM-1W adapter. This lab specifies the **WPC300N** (a Linksys-branded 802.11n wireless PC card). Both provide wireless connectivity, but the WPC300N is designed to pair specifically with the WRT300N router. In practice, any 802.11-compatible adapter will work with any compatible access point — the SSID and security settings are what determine connectivity, not the adapter brand.

> **📸 Screenshot Suggestion:** Capture the laptop's Physical tab with the WPC300N adapter installed.

### Step 5 – Name your devices

14. Click the **WRT300N** wireless router → **Config** tab. In the **Display Name** field, type a personalized name (e.g., `Andrine's Wireless Router`).
15. Click the **Laptop** → **Config** tab → **Display Name** → enter a personalized name (e.g., `Andrine's Laptop`).
16. Click the **Tablet PC** → **Config** tab → **Display Name** → enter a personalized name (e.g., `Andrine's Tablet`).

> **📝 Note – Why personalize device names?**  
> This is a grading requirement — your instructor needs to verify that the screenshots belong to you. In production environments, naming conventions serve a more critical purpose: network documentation. Descriptive hostnames like `FL-JAX-SW01` (Florida, Jacksonville, Switch 01) help administrators identify devices during troubleshooting. Consistent naming is a fundamental part of network management.

### Step 6 – Configure the SSID on the wireless router

17. Click the **WRT300N** → **GUI** tab → **Wireless** → **Basic Wireless Settings**.
18. Change the **SSID** to something unique (e.g., `Andrine-Secure`).
19. Scroll down and click **Save Settings**.

### Step 7 – Connect devices to the wireless network (NO security yet)

> **💡 Pro Tip:** Get all devices connected and pinging **before** applying security settings. This confirms that the basic wireless connectivity works, so if something breaks after adding security, you know the issue is in the security configuration — not the underlying network.

20. Click the **Laptop** → **Desktop** tab → **PC Wireless** → **Connect** tab. Your SSID should appear in the list. Click on it and select **Connect**.
21. Click the **Tablet PC** → **Config** tab → **Wireless0** → enter the same SSID in the SSID field.

Wireless signal indicators should appear between both devices and the WRT300N.

> **📸 Screenshot Suggestion:** Capture the workspace showing all three devices with wireless connections active (before security is applied). *This is Documentation 1 — "network working."*

### Step 8 – Verify IP addresses and test connectivity

22. On the **WRT300N**, go to **GUI** tab → **Setup** to confirm the router IP is **192.168.0.1**.
23. On the **Laptop**, go to **Desktop** tab → **IP Configuration** and note the assigned IP (e.g., 192.168.0.100).
24. On the **Tablet PC**, check the **Config** tab for its assigned IP.
25. From the **Laptop**, open **Desktop** tab → **Command Prompt** and ping the router:
    ```
    ping 192.168.0.1
    ```
26. Also ping the tablet's IP address to confirm full connectivity.

> **📝 Note – Understanding the ping test:**  
> The `ping` command sends **ICMP Echo Request** packets to a target IP and listens for **Echo Reply** packets. A successful ping confirms:
> - **Layer 1:** Physical/wireless connectivity exists.
> - **Layer 2:** The wireless association (SSID match) is working.
> - **Layer 3:** IP addressing is correct — both devices are on the same 192.168.0.0/24 subnet.
>
> The IP addresses in this lab follow the same scheme as Module 10:
>
> | Device | Expected IP | How Assigned |
> |---|---|---|
> | WRT300N | 192.168.0.1 | Factory default (static) |
> | Laptop | 192.168.0.100+ | DHCP from router |
> | Tablet PC | 192.168.0.100+ | DHCP from router |
>
> All share subnet mask **255.255.255.0**, meaning:
> - **Network:** 192.168.0 (first 3 octets) — identifies the subnet
> - **Host:** last octet — identifies the individual device
> - Since all devices share the same network portion, they can communicate directly without routing.

> **📸 Screenshot Suggestion:** Capture the Command Prompt showing a successful ping from the laptop to the wireless router (192.168.0.1). *This is Documentation 2.*

---

## Part 2: Apply Wireless Security

### Step 9 – Configure security on the wireless router

27. Click the **WRT300N** → **GUI** tab → **Wireless** → **Wireless Security**.
28. Choose one of the following security modes:

| Security Mode | Configuration |
|---|---|
| **WEP** | Select WEP → enter a WEP Key (e.g., `0123456789`) |
| **WPA Personal** | Select WPA Personal → Encryption: TKIP → enter a Passphrase (e.g., `0123456789`) |
| **WPA2 Personal** | Select WPA2 Personal → Encryption: AES → enter a Passphrase (e.g., `0123456789`) |

29. Click **Save Settings**.

> **📝 Note – Wireless security protocols explained:**  
>
> | Protocol | Encryption | Key Length | Security Level | Status |
> |---|---|---|---|---|
> | **WEP** | RC4 stream cipher | 64 or 128-bit | ❌ Broken — crackable in minutes | Deprecated; avoid in production |
> | **WPA Personal** | TKIP (Temporal Key Integrity Protocol) | 128-bit | ⚠️ Improved, but TKIP has known weaknesses | Legacy; being phased out |
> | **WPA2 Personal** | AES-CCMP | 128-bit | ✅ Strong — current standard | Recommended minimum |
>
> For this lab, any of the three will satisfy the requirement. For Skills Test 3, you should be comfortable configuring **all three** — the test may specify which one to use.
>
> **"Personal" vs. "Enterprise":**
> - **Personal** (PSK — Pre-Shared Key): All users share the same passphrase. Suitable for home and small office networks.
> - **Enterprise** (802.1X/RADIUS): Each user authenticates individually against a RADIUS server. Used in corporate environments. This lab uses Personal mode.
>
> **Why is the passphrase "0123456789" acceptable here?**  
> It's easy to type during a timed lab or skills test. In a real deployment, you would use a strong passphrase (12+ characters, mixed case, numbers, symbols). The passphrase is used to derive the encryption key — a weak passphrase makes the network vulnerable to dictionary attacks.

> **📸 Screenshot Suggestion:** Capture the Wireless Security settings page on the WRT300N GUI tab showing your chosen security mode and the configured key/passphrase. *This is one option for Documentation 3 or 4.*

### Step 10 – Configure security on the laptop

30. Click the **Laptop** → **Desktop** tab → **PC Wireless** → **Connect** tab.
31. Your SSID may show as disconnected after the security change. Click on the SSID and select **Connect**.
32. A security prompt appears — enter the **same key/passphrase** you set on the router and select the matching security type.

**Alternative method (Profile tab):**

33. On the **PC Wireless** window, select the **Profiles** tab.
34. Create a new profile with the SSID name, select the correct security type, and enter the passphrase.

> **📸 Screenshot Suggestion:** Capture either the **Connect** tab or the **Profiles** tab showing the security settings applied to the laptop. *This is another option for Documentation 3 or 4.*

### Step 11 – Configure security on the tablet

35. Click the **Tablet PC** → **Config** tab → **Wireless0** from the left menu.
36. Set the **Authentication** to match the router (WEP, WPA-PSK, or WPA2-PSK).
37. Enter the same **key or passphrase**.

The wireless signal should re-establish between the tablet and the router.

> **📝 Note – Security must match on all devices:**  
> The security protocol (WEP/WPA/WPA2), encryption type (TKIP/AES), and passphrase must be **identical** across the access point and every client. If any parameter is mismatched, the device will fail to associate. This is the most common source of errors when applying wireless security — double-check that the security mode and passphrase are exactly the same on the router, laptop, and tablet.

> **📸 Screenshot Suggestion:** Capture the tablet's Config tab → Wireless0 showing the applied security settings. *This is another option for Documentation 3 or 4.*

### Step 12 – Verify connectivity after security is applied

38. From the **Laptop**, open **Desktop** tab → **Command Prompt**.
39. Ping the router:
    ```
    ping 192.168.0.1
    ```
40. Ping the tablet's IP address.
41. From the **Tablet**, open **Desktop** tab → **Command Prompt** and ping the laptop's IP.

All pings should succeed, confirming that the wireless security is correctly configured and all devices can still communicate.

> **📝 Note – What changed with security enabled?**  
> At the IP layer (Layer 3), nothing changed — the devices still have the same IP addresses on the same 192.168.0.0/24 subnet. What changed is at **Layer 2**: all wireless frames are now **encrypted** before transmission. An attacker sniffing the wireless traffic would see encrypted data instead of plaintext. The ping test confirms that the encryption/decryption is working correctly on both ends.

> **📸 Screenshot Suggestion:** Capture a successful ping from the laptop to the router after security has been applied. This serves as additional verification that the secured network is fully functional.

---

## Submission Checklist

Upload the following screenshots:

| # | Documentation | What to Capture |
|---|---|---|
| 1 | Network working | Full workspace showing all devices connected wirelessly |
| 2 | Successful ping | Command Prompt showing ping from laptop to wireless router (192.168.0.1) |
| 3 | Security proof (pick 1) | Laptop Connect tab, Laptop Profiles tab, Tablet Config tab, OR Router Wireless Security page |
| 4 | Security proof (pick 1) | A *different* option from the list above |

---

## Summary

This lab extended the wireless networking skills from Module 10 by adding **wireless security**:

| Phase | What You Did | Why |
|---|---|---|
| Build | Placed WRT300N, laptop (with WPC300N), and tablet | Create the physical/wireless topology |
| Name | Personalized device display names | Grading identification; mirrors production naming conventions |
| Connect | Matched SSIDs across all devices | Established Layer 2 wireless association |
| Verify | Pinged between devices | Confirmed Layer 3 connectivity before adding security |
| Secure | Applied WEP/WPA/WPA2 on router and all clients | Encrypted wireless traffic at Layer 2 |
| Re-verify | Pinged again after security | Confirmed encryption doesn't break connectivity |

### IP Address Map

| Device | IP Address | Network Portion | Host Portion |
|---|---|---|---|
| WRT300N | 192.168.0.1 | 192.168.0 | .1 |
| Laptop | 192.168.0.100+ | 192.168.0 | .100+ |
| Tablet | 192.168.0.100+ | 192.168.0 | .100+ |

All on subnet **192.168.0.0/24** (mask 255.255.255.0) — 254 usable host addresses, gateway at .1.

---

## Key Networking Concepts Reinforced

| Concept | How It Applied |
|---|---|
| **WEP / WPA / WPA2** | Configured and compared three wireless security protocols |
| **Pre-Shared Key (PSK)** | All devices share the same passphrase for authentication |
| **SSID + Security matching** | Both the network name and security settings must be identical across all devices |
| **Layered troubleshooting** | Connected without security first, then added security — isolating potential issues |
| **ICMP ping** | Verified Layer 3 reachability before and after security changes |
| **DHCP** | Router auto-assigned IP addresses to wireless clients |
| **Network vs. host portion** | 192.168.0.x — first 3 octets are the network, last octet identifies the device |

---

## Skills Test 3 Preparation Notes

For the skills test, practice all three security types until you can configure them quickly:

1. **Start with no security** — get the network connected and pinging first.
2. **Apply security on the router** (GUI tab → Wireless → Wireless Security).
3. **Match security on each client** — the laptop uses Desktop → PC Wireless → Connect/Profiles; the tablet uses Config → Wireless0.
4. **Use a simple passphrase** like `0123456789` during the test — saves time and avoids typos.
5. **Always re-ping after applying security** to confirm nothing broke.
