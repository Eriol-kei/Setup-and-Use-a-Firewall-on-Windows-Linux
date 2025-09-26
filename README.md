# Setup-and-Use-a-Firewall-on-Windows-Linux
Configure and test basic firewall rules to allow or block traffic.

Configure and test basic firewall rules to allow or block traffic.

## Tools Used
- **UFW (Uncomplicated Firewall)** on Linux
- **netcat (nc)** for testing connections

---

Configure and test basic firewall rules to allow or block traffic.

## Tools Used
- UFW (Uncomplicated Firewall) on Linux
- netcat (nc) for testing connections

---

## Steps Performed

1. Install and enable UFW
   sudo apt update
   sudo apt install ufw -y

2. Check current firewall status and rules
   sudo ufw status verbose

3. Allow SSH (port 22) before enabling firewall
   sudo ufw allow 22/tcp
   sudo ufw enable

4. Add a rule to block inbound traffic on port 23 (Telnet)
   sudo ufw deny 23/tcp

5. Verify rules
   sudo ufw status numbered

6. Test the firewall rule  
   Start a test connection to port 23:
   nc -vz localhost 23  
   Expected Result: Connection should fail (blocked by firewall).

7. Allow SSH explicitly (for safety)
   sudo ufw allow 22/tcp

8. Remove the test block rule (restore original state)
   sudo ufw delete deny 23/tcp

9. Final check
   sudo ufw status verbose
