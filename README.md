# Setup-and-Use-a-Firewall-on-Windows-Linux
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
   ```bash
   sudo apt update
   sudo apt install ufw -y

3. Check current firewall status and rules
   ```bash
   sudo ufw status verbose

5. Allow SSH (port 22) before enabling firewall
   ```bash
   sudo ufw allow 22/tcp
   sudo ufw enable

7. Add a rule to block inbound traffic on port 23 (Telnet)
   ```bash
   sudo ufw deny 23/tcp

9. Verify rules
    ```bash
   sudo ufw status numbered
    ```

10. Test the firewall rule 
   Start a test connection to port 23:
```bash
nc -vz localhost 23  
   Expected Result: Connection should fail (blocked by firewall)
```

12. Allow SSH explicitly (for safety)
```bash
   sudo ufw allow 22/tcp
```
12. Remove the test block rule (restore original state)
```bash
   sudo ufw delete deny 23/tcp
```

15. Final check
```bash
   sudo ufw status verbose
