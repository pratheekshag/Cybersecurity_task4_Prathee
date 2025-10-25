# Cybersecurity_task4_Prathee
Setup and Use a Firewall on Windows/Linux
# Firewall Configuration and Testing Guide

## 🪟 Windows Firewall Steps

1. Open Firewall Configuration Tool
- Press `Win + R` → type `wf.msc` → hit Enter 
  *(or open from Control Panel → System and Security → Windows Defender Firewall → Advanced Settings)*

2. List Current Firewall Rules
GUI Method:
- Go to Inbound Rules or Outbound Rules to view all entries.

Command Line:
```bash
netsh advfirewall firewall show rule name=all

3. Add Rule to Block Inbound Traffic on Port 23 (Telnet)
GUI Method:
- Click New Rule → Port → TCP → Specific local ports: 23
- Choose Block the connection
- Apply to all profiles → Name it "Block Telnet"
Command Line:
netsh advfirewall firewall add rule name="Block Telnet" dir=in action=block protocol=TCP localport=23

4. Test the Rule
Use Nmap to test:
nmap -p 23 localhost
Result → Port appears closed (sometimes filtered).

5. Remove Test Rule
netsh advfirewall firewall delete rule name="Block Telnet"
