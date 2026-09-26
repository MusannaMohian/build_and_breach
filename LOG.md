# Build & Breach - Session Log

## 2026-09-24 - M1: Host readiness check
- **Did:** Checked host specs (16 GB RAM, i7-1260P, virtualization enabled). Found high idle memory; traced it to Chrome and Splunk.
- **Why it worked / failed:** Chrome runs a separate process per tab and extension, so closing tabs freed memory directly. Splunk and MySQL were set to Automatic startup, so they ran at every boot even when unused. Switching them to Manual stops that.
- **Still don't understand:** If dual-boot pc of my home network should be added to this project or not.

## 2026-09-26 - M3: Kali attacker VM
- **Did:** Reused existing Kali, reverted to Inintial snapshot for clean baseline. Moved to VMnet2, set static 10.10.10.10/24 with no gateway, updated once via NAT then disconnected. Took kali-lab-ready snapshot.
- **Why it worked:** No default route allowing the attacker Kali to be diconnected from the internet. It is maintaing the islation traits of the project. The network adapter in default looks for a DHCP address. But VMnet2 was set as static, which gives us more control over the network and prevents accidental mishaps with real-world IPs. So the attacker Kali is now set with a static IP address over VMnet2.
- **Cursor issue:** The cursor in Kali vm was invisible inside the screen. The issue was the hardware compatinility was set to lower versions. Once updated to 25H or later, it is visible again.
- **Stil don't understand:** How SHA256 verification works and what it doesn't cover?