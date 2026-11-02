   ###Man-in-the-Middle (MITM) Attack Detection###
Hands-on Cybersecurity Learning | Network Security Monitoring

Overview
Today, I explored Man-in-the-Middle (MITM) attacks and learned how attackers can intercept, monitor, or manipulate communication between two parties without their knowledge.
A MITM attack occurs when an attacker positions themselves between a communicating client and server, potentially allowing them to eavesdrop on sensitive information, manipulate transmitted data, or redirect network traffic.
These attacks may expose sensitive information such as login credentials, session tokens, and financial data, particularly when encryption or authentication mechanisms are weak or improperly configured.

As part of this learning exercise, I explored three common MITM techniques:
•	ARP Spoofing (Network Interception)
•	DNS Spoofing (Traffic Redirection)
•	SSL Stripping (Downgrade Attack)
I also explored the network indicators that can help identify potential MITM activity through traffic analysis.

##1. ARP Spoofing (Network Interception)

What I Learned
ARP spoofing is a technique in which an attacker sends forged Address Resolution Protocol (ARP) messages to associate their MAC address with the IP address of another device, such as the default gateway.
This can cause network traffic intended for the legitimate gateway to be redirected through the attacker's device, potentially enabling traffic interception or manipulation.

Indicators of Attack (IoAs)
During network traffic analysis, the following indicators may suggest potential ARP spoofing activity:
•	Duplicate IP-to-MAC Mappings: Multiple MAC addresses associated with the same IP address, particularly the default gateway IP.
•	Unsolicited ARP Replies: ARP replies received without a corresponding request.
•	Abnormal ARP Traffic Volume: A sudden increase in ARP requests or replies within a short period.
•	Unusual Traffic Routing: Network traffic redirected through an unexpected MAC address.
•	Gateway Redirection Patterns: Changes in the MAC address associated with the default gateway.
•	Repeated ARP Announcements: Frequent ARP messages advertising unexpected IP-to-MAC address mappings.

**Detection Approach**
I explored how ARP traffic can be analyzed to identify duplicate IP-to-MAC address mappings.
By examining ARP requests and replies, I learned how to identify situations where multiple MAC addresses claim the same IP address, which may indicate ARP spoofing.

Key Learning: Monitoring ARP traffic and identifying unexpected changes in IP-to-MAC address mappings can help detect potential network interception attempts.

**Wireshark Analysis**
Useful display filters:
arp
To identify ARP replies:
arp.opcode == 2
To investigate ARP traffic associated with a specific IP address:
arp.src.proto_ipv4 == 192.168.1.1
Replace 192.168.1.1 with the IP address of your default gateway.
📸 Screenshot: ARP traffic analysis showing duplicate IP-to-MAC address mappings.
<img width="940" height="364" alt="image" src="https://github.com/user-attachments/assets/ef752517-378a-40fa-bcc6-4cb1cc8470a7" />
<img width="940" height="576" alt="image" src="https://github.com/user-attachments/assets/924651fc-a4b0-4faf-9e76-613b8b489dd1" />


#2. DNS Spoofing (Traffic Redirection)#
What I Learned
DNS spoofing is a technique in which an attacker provides forged DNS responses to redirect a victim to an unintended IP address.
By manipulating DNS resolution, an attacker may redirect users to malicious websites, phishing pages, or systems controlled by the attacker.
DNS spoofing can be used as part of a Man-in-the-Middle attack to intercept or manipulate communication.

**Indicators of Attack (IoAs)**
The following indicators may suggest potential DNS spoofing activity:
•	Multiple DNS Responses: Multiple conflicting responses to the same DNS query, particularly when they contain different IP addresses.
•	Unexpected DNS Response Sources: DNS responses received from IP addresses that are not part of the expected DNS infrastructure.
•	Unusual TTL Values: Unexpectedly low Time-to-Live (TTL) values that may indicate suspicious DNS behavior.
•	Unsolicited DNS Responses: DNS responses received without a corresponding client query.
•	Unexpected DNS Resolution: A domain resolving to an unfamiliar or suspicious IP address.

**Detection Approach**
I explored how DNS responses can be investigated by examining their source IP addresses and comparing them with the organization's configured DNS resolvers.
By identifying DNS responses originating from unexpected sources, I learned how to investigate potential DNS spoofing and redirection attempts.
Key Learning: Monitoring DNS response sources, comparing DNS answers, and identifying unexpected domain resolutions can help detect potential DNS spoofing.

**Wireshark Analysis**
To inspect DNS traffic:
dns
To identify DNS responses:
dns.flags.response == 1
To investigate DNS responses from an unexpected DNS server:
dns.flags.response == 1 && ip.src != 192.168.1.1
Replace 192.168.1.1 with your configured DNS resolver.
Note: This filter is useful for investigation, but it may also identify legitimate DNS responses. Unexpected DNS sources should be validated against the network's DNS configuration.
📸 Screenshot: DNS response analysis and identification of unexpected DNS response sources.
<img width="940" height="184" alt="image" src="https://github.com/user-attachments/assets/48364fc6-0939-4f37-9ebb-6bd589c46e06" />
**
#3. SSL Stripping (HTTPS Downgrade Attack)#
What I Learned
SSL stripping is a type of Man-in-the-Middle attack in which an attacker attempts to downgrade a victim's secure HTTPS connection to an unencrypted HTTP connection.
This can occur when a victim initially connects to a website over HTTP and the attacker intercepts the communication before a secure HTTPS connection is established.
By manipulating the connection, the attacker may be able to observe sensitive information transmitted over HTTP, such as login credentials or session data.

**Indicators of Attack (IoAs)**
The following indicators may suggest potential SSL stripping activity:
•	Unexpected HTTP Connections: Communication with websites that should normally use HTTPS but are accessed over HTTP.
•	HTTPS Downgrade: A secure HTTPS connection is redirected or downgraded to HTTP.
•	Missing HTTPS Redirection: Websites fail to enforce secure HTTPS connections.
•	Suspicious HTTP Traffic: Sensitive information transmitted through unencrypted HTTP requests.
•	Certificate or Connection Anomalies: Unexpected changes in the security properties of a connection.

**Detection Approach**
I explored how unencrypted HTTP traffic can expose sensitive information when secure communication is not properly enforced.
By examining HTTP requests and identifying communication that should have been protected by HTTPS, I learned how to investigate potential SSL stripping attacks.
Key Learning: Monitoring unexpected HTTP traffic and validating HTTPS enforcement can help identify potential downgrade attacks.

**Wireshark Analysis**
To identify HTTP traffic:
http
To investigate HTTP requests:
http.request
To identify HTTP traffic containing a login-related URI:
http.request.uri contains "login"
This filter helps identify HTTP requests containing the word login in their URI. It does not independently confirm SSL stripping.
📸 Screenshot: HTTP traffic analysis showing potentially unencrypted communication.
<img width="940" height="158" alt="image" src="https://github.com/user-attachments/assets/33da63a8-e0f4-494e-ad39-5ddeb9d66afb" />


**Tools and Technologies Used**
Tool	Purpose
Wireshark	Network traffic analysis and packet inspection
ARP	Investigating IP-to-MAC address mappings
DNS	Analyzing DNS responses and potential spoofing
HTTP/HTTPS	Investigating secure and unencrypted communication
Network Security Monitoring	Identifying potential MITM indicators

**Key Takeaways**
Through today's hands-on cybersecurity learning session, I gained practical exposure to:
•	Understanding Man-in-the-Middle attack techniques.
•	Identifying suspicious ARP traffic and duplicate IP-to-MAC mappings.
•	Investigating potential ARP spoofing activity.
•	Analyzing DNS responses for potential spoofing and redirection.
•	Understanding SSL stripping and HTTPS downgrade attacks.
•	Using Wireshark display filters to investigate suspicious network traffic.
•	Identifying network indicators of compromise (IoCs).
This learning exercise strengthened my understanding of network security monitoring, traffic analysis, and the detection of potential Man-in-the-Middle at
