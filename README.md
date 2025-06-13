
# Web Application Security Project

## Task 1: DVWA Attacks on Metasploitable VM

**IP Address:** `192.168.150.131`

### 1. Privilege Escalation (via DVWA)
- Navigate to DVWA (Damn Vulnerable Web Application) by entering the IP in a browser.
- Explore features to identify potential vulnerabilities.
- Exploit DVWA features like insecure settings to gain access or escalate privilege.

### 2. CSRF (Cross Site Request Forgery)
- Action: Change password to "password1".
- Observations:
  - When changing the password, the URL contains both the new and confirmed password.
  - Copying and altering this URL in a new tab still processes the request – a CSRF vulnerability.

### 3. SQL Injection
- Input `2` in the user ID field: Returns first name and surname of ID 2.
- Input `2' OR 'X' = 'X` – Returns all users’ names.
- Input `1' OR '1' = '1' UNION SELECT user, password FROM users #` – Displays usernames and hashed passwords.
- Use https://www.crackstation.net/ to crack hash values.

### 4. XSS (Cross Site Scripting)
- Input `<script>alert("this is me")</script>` in a form field.
- Result: JavaScript popup appears – proving XSS vulnerability.

### Tools Used:
- **Burp Suite** and **OWASP ZAP** for intercepting and modifying requests.

---

## Task 2: Zone Alarm Firewall Setup & Testing

### Setup:
- Download and install **Zone Alarm Firewall** on Windows VM.
- Confirm baseline connectivity: `nmap -sP 192.168.150.129` from Kali VM.
- In ZoneAlarm: Go to **Advanced Settings > Zones > Add Host**.
- Add Kali Linux IP and **set to Block**.

### Results:
- Kali terminal shows: `Host seems down` after blocking.
- ZoneAlarm logs confirm the block.

### Extra:
- **Facebook block test**:
  - Add `www.facebook.com` as a blocked host.
  - Browser access fails as expected.

---

## Task 3: Shodan Exploration

### Vulnerable Webcams
- Used Shodan with filters like `netcam`, `port:554`, `country:US`, etc.
- Screenshots reveal live and unsecured webcam feeds globally.

### Web Application Firewall Detection
- Searched for services behind WAFs like **Cloudflare** and **Amazon EC2**.
- Shodan results show headers and metadata indicating presence of WAF protection.

---

## Conclusion
This project demonstrated:
- Exploitation of common web app vulnerabilities via DVWA.
- Firewall configuration and network traffic control using Zone Alarm.
- Use of Shodan to uncover real-world vulnerabilities and WAF protection mechanisms.
