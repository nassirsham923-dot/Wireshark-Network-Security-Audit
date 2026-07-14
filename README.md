# Wireshark Cryptography Audit: HTTP vs. HTTPS

## Project Overview
This project demonstrates the security differences between unencrypted (HTTP) and encrypted (HTTPS/TLS) web traffic using Wireshark. By capturing and analyzing network packets, I demonstrated how credentials can be intercepted in plain text over HTTP, and how TLS 1.3 protects sensitive data over HTTPS.

## Objectives
* Capture and analyze live network traffic using Wireshark.
* Filter traffic to isolate specific protocol actions (HTTP POST vs. TLS).
* Compare clear-text data transmission with encrypted ciphertext.
* Document security findings and remediation steps.

## Technical Walkthrough

### Part 1: Unencrypted Traffic Analysis (HTTP)
* **Goal:** Capture a login attempt on an unsecure website (`http://demo.testfire.net`).
* **Filter Used:** `http.request.method == "POST"`
* **Finding:** The credentials were fully exposed in plain text.

![HTTP Clear Text Screenshot](screenshots/http_cleartext.png)

### Part 2: Encrypted Traffic Analysis (HTTPS/TLS)
* **Goal:** Capture a login attempt on a secure website using HTTPS.
* **Filter Used:** `tls`
* **Finding:** The handshake (`Client Hello` / `Server Hello`) was visible, but the login payload was completely encrypted as scrambled `Application Data`.

![HTTPS Encrypted Screenshot](screenshots/https_encrypted.png)

## Key Takeaways
1. **Clear Text Vulnerability:** Unencrypted HTTP protocols leave user credentials exposed to local packet sniffing attacks.
2. **TLS Protection:** Upgrading to HTTPS ensures confidentiality and integrity by usin
