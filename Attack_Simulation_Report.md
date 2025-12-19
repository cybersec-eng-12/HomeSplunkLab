# Scenario: Internal Network Reconnaissance & Brute Force

### Attacker: Kali Linux (IP: 192.168.86.29)
### Victim: 2 Windows 11 Endpoints: Win-Client-01(IP: 192.168.86.26) & Win-Client-02(IP: 192.168.86.32) 

## Attack 1: Nmap Port Scan

**Command Used**: `nmap -sT -T5 -p- <Windows-Victim-IP>`

**Detection**: Detected via Sysmon Event ID 3. Observed between 56 attempts on Win-Client-01 & 82 connection attempts on Win-Client-02 from Attacker IP within 20 seconds.

**Evidence**: 

<img width="2536" height="386" alt="nmap_scan_being_detected" src="https://github.com/user-attachments/assets/6d89347e-2a41-49cc-8e99-534e846cad4d" />

## Attack 2: RDP Brute Force

**Command Used**: `hydra -l localadmin passlist.txt rdp://192.168.86.26`

**Detection**: Detected via Windows Event ID 4625.

**Evidence**: 
<img width="2554" height="357" alt="image" src="https://github.com/user-attachments/assets/de03e108-f1fa-425e-bc5a-7b7635489e6a" />

**Conclusion**:
The SIEM successfully ingested logs from endpoints, identifying both the scanning activity and an active brute-force attack. Future improvements could include automated IP blocking via firewall integration or automatic account disabling with Active Directory integration.

