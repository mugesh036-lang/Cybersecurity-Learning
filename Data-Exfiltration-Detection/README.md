
# Data Exfiltration Detection

## Overview

Today, I explored different data exfiltration techniques and learned how to identify suspicious network traffic using Wireshark and Splunk.

This hands-on learning session focused on understanding common data exfiltration methods, identifying indicators of attack, and analyzing suspicious network traffic.

## Topics Covered
- DNS tunneling detection
- FTP-based data exfiltration
- HTTP-based data exfiltration
- ICMP-based data exfiltration

## 1. DNS Tunneling Detection

### Learning Objective

Understand how attackers can use DNS queries to transfer data covertly and how suspicious DNS traffic can be identified.

### Indicators of Attack

- Unusually long DNS queries
- Suspicious or encoded subdomains
- High volumes of DNS requests
- Unusual DNS communication patterns

### Tools Used

- Wireshark
- Splunk

### Key Learning

I analyzed DNS traffic and identified unusually long, suspicious-looking DNS queries.

These observations helped me understand how abnormal DNS query lengths and suspicious communication patterns can indicate potential DNS tunneling.

### Screenshot

<img width="1299" height="450" alt="image" src="https://github.com/user-attachments/assets/84f8f1e4-c0f9-439b-8199-5cf7ff6dc775" />
<img width="1287" height="104" alt="image" src="https://github.com/user-attachments/assets/707cd7b6-bf83-4d0f-a8e3-a6aeebf506e7" />


## 2. FTP-Based Data Exfiltration

### Learning Objective

Understand how FTP can be used to transfer sensitive files and how suspicious file transfers can be investigated.

### Wireshark Filter

```wireshark
ftp && frame.len > 90
```

### Key Learning

I explored FTP traffic filtering and learned how to investigate suspicious file transfers, file extensions, and unusually large packets.

### Screenshot

<img width="924" height="760" alt="image" src="https://github.com/user-attachments/assets/7b5705ed-15d0-4666-8bb1-8228cec39f5e" />
<img width="1099" height="126" alt="image" src="https://github.com/user-attachments/assets/7f324eb9-ab8d-45b9-ae59-badfbeb9ecfe" />
<img width="1089" height="221" alt="image" src="https://github.com/user-attachments/assets/9a2789a0-7774-4d4b-899c-fa1ebd8113bd" />


## 3. HTTP-Based Data Exfiltration

### Learning Objective

Identify suspicious HTTP traffic that may indicate unauthorized data uploads.

### Common Indicators

- Unusually large HTTP POST requests
- Unexpected external destinations
- Suspicious outbound data transfers
- Repeated communication with unfamiliar hosts

### Key Learning

I explored how large HTTP POST requests and unusual outbound traffic patterns can help identify potential data exfiltration attempts.

### Screenshot
<img width="1116" height="401" alt="image" src="https://github.com/user-attachments/assets/6358051b-93a3-43c0-8ca3-7bcac817e2b2" />
<img width="1113" height="250" alt="image" src="https://github.com/user-attachments/assets/1ebffc1c-d5c3-4e09-94b3-6f19ca4ffb85" />
<img width="1096" height="117" alt="image" src="https://github.com/user-attachments/assets/861cf5c6-59e0-4ff4-93d1-904dc9779375" />
<img width="1094" height="615" alt="image" src="https://github.com/user-attachments/assets/f72f5fd8-2da6-4d8a-8c56-a665f9ffaf86" />



## 4. ICMP-Based Data Exfiltration

### Learning Objective

Understand how ICMP packets can be abused to transfer data and how suspicious ICMP traffic can be identified.

### Wireshark Filter

```wireshark
icmp.type == 8 && frame.len > 100
```
<img width="1102" height="439" alt="image" src="https://github.com/user-attachments/assets/f6dd46f8-aa96-4c3c-b6d2-617c69e22eb3" />

### Indicators of Attack

- Unusually large ICMP packets
- Persistent ICMP communication
- Suspicious payload contents
- Unusual communication with external hosts

### Key Learning

I analyzed ICMP Echo Request packets and explored how unusually large packet sizes and suspicious payloads may indicate potential ICMP tunneling.

### Screenshot

<img width="1098" height="491" alt="image" src="https://github.com/user-attachments/assets/170858a7-2789-46d5-be8c-ceff2c488165" />


## Tools and Technologies

- Wireshark
- Splunk
- Network Traffic Analysis
- Threat Detection
- Security Monitoring

## Key Takeaways

Through this hands-on learning session, I gained practical exposure to:

- Identifying suspicious DNS queries
- Investigating FTP traffic
- Analyzing HTTP POST requests
- Detecting abnormal ICMP traffic
- Using Wireshark display filters
- Understanding network indicators of compromise

This exercise strengthened my understanding of network-based threat detection and data exfiltration analysis.

---

**Learning Journey:** Cybersecurity  
**Topic:** Data Exfiltration Detection  
**Tools:** Wireshark and Splunk
