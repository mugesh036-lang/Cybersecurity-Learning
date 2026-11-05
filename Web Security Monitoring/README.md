# Web Security Monitoring



## Essentials of web security


**Protecting the Application**

•	Secure Coding: Avoid insecure functions, ensure proper handling of errors, and remove sensitive information.

•	Input Validation & Sanitization: Validate and sanitize user input to prevent injection attacks.

•	Access Control: Restrict access based on user roles.



**Protecting the Web Server**


•	Logging: Keep a detailed record of all web requests with access logs.

•	Web Application Firewall (WAF): Filter and block harmful traffic based on defined rules.

•	Content Delivery Network (CDN): Reduce direct exposure to your server and use integrated WAFs.



**Protecting the Host Machine**

•	Least Privilege: Use low-privilege users for services.

•	System Hardening: Disable unnecessary services and close unused ports.

•	Antivirus: Add endpoint-level protection that blocks known malware.



**Security Tips for All Three Components**

•	Strong Authentication: Don't just let anyone access your code, admin panels, or host machine.

•	Patch Management: Ensure your app dependencies, web server, and host machine are up to date.



**Content Delivery Network (CDN)**

CDNs store and serve cached content from servers closer to the user to reduce latency.


**Security Benefits**

•	IP Masking: Hides the origin server IP address, which makes it harder for attackers to target.

•	DDoS Protection: CDNs can absorb a large amount of traffic, making denial-of-service attacks less effective.

•	Enforced HTTPS: Encrypted communication via TLS is enforced by default by most CDNs.

•	Integrated WAF: Many CDNs, including Cloudflare CDN, Amazon CloudFront & Azure Front Door, integrate web application firewalls



**Web Application Firewall (WAF)**

They inspect incoming HTTP traffic and block or log potentially harmful requests based on security rules

•	Cloud-based (Reverse Proxy): Sits in front of the web server. These WAFs are easy to deploy and have great scalability. 

•	Host-based: Software deployed directly on the web server and offers control for each application. 

•	Network-based: A physical or virtual appliance situated on the network perimeter. More suited for enterprise environments.




## Detecting Web Attacks

**Client-side**
attacks rely on abusing weaknesses in user behavior or on the user's device. 

The tools available to an analyst, such as server-side logs and network traffic captures, offer little to no visibility into what occurs inside a user's browser without EDR

Common Client-Side Attacks: Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), 

**Server-side**

Attacks rely on exploiting vulnerabilities within a web server, the application's code, or the backend that supports a website or a web application.

we will identify server-side attacks in both logs and network traffic.

Common Server-Side Attacks: Brute-force , SQL Injection (SQLi), Command Injection 

**Log-based analysis**

Logs can be a valuable tool for detecting web attacks.  Every request sent to a web server can leave evidence in its access and error logs.

**Network traffic logs**

allows analysts to examine the raw data exchanged between a client and a server. By capturing and inspecting packets, analysts can observe attack behavior on a more detailed level, including the underlying transport protocols and the application data itself. Network captures are more verbose than server logs, revealing the data behind every request and response. This can include full HTTP headers, POST bodies, cookies, and uploaded and downloaded files

**Web Application Firewalls (WAFs) **

WAF are often the first line of defense for websites and web applications. So far in this room, we have focused on detecting and analyzing malicious activity

Challenge-Response Mechanisms – Request with captcha

Integrating Known Indicators and Threat Intelligence --- OWASP Top 10, CVE, APT groups

Rule:

If User-Agent contains "sqlmap"

then BLOCK



