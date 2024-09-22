# Web application testing:

# Step 1: Understand the Tools for Web Application Testing

There are many tools pre-installed on Kali Linux. Here are some essential ones for beginners:

* OWASP ZAP: An easy-to-use tool for finding vulnerabilities in web applications.

* Burp Suite: A powerful web vulnerability scanner with a user-friendly interface.

* Nmap: A network scanner that can be used to detect open ports and services.

* Nikto: A web server scanner that identifies potential vulnerabilities.

* SQLmap: Used for automated testing of SQL injection vulnerabilities.

* Dirb: A directory brute-force tool.

* Wpscan: A WordPress vulnerability scanner.

# Step 2: Basic Reconnaissance and Scanning

* Nmap: Scan for Open Ports: Use Nmap to scan for open ports on the target web application’s server. This helps identify services that might be running.

* nmap -sV -p- <target-ip>
* -sV: Detect version of services running on ports.
* -p-: Scan all ports (1-65535).

Directory Brute-Force with Dirb: Use Dirb to find hidden directories on a web server.

* dirb http://<target-ip>/
  
This tool will try to brute-force and identify hidden or unlisted directories/files.

* Nikto: Scan Web Server for Vulnerabilities: Nikto scans web servers and identifies potential vulnerabilities such as outdated software or insecure configurations.

* nikto -h http://<target-ip>/

# Step 3: Web Application Testing with OWASP ZAP

Launch OWASP ZAP: Open ZAP by typing:

* zaproxy

* ZAP is a proxy-based tool that captures web traffic between your browser and the server. It allows you to inspect and manipulate requests.

Set Up Browser Proxy:

* In ZAP, configure the proxy by going to Tools -> Options -> Local Proxies. Make sure the default proxy (usually 127.0.0.1:8080) is set.
In your browser, configure the proxy settings to forward traffic through 127.0.0.1:8080.
* Spider the Web Application:

* In ZAP, use the Spider feature to crawl and map the web application.
Right-click on the target web application in the Sites tree, then choose Spider -> Attack.
ZAP will automatically crawl and map out the web application for testing.
* Scan for Vulnerabilities:

After the spider has finished crawling, right-click on the target and select Active Scan -> Attack.
ZAP will perform an active scan of the target and report any discovered vulnerabilities.

# Step 4: Manual Testing with Burp Suite
Launch Burp Suite: Open Burp Suite by typing:

* burpsuite

* Set Up Proxy: Similar to ZAP, Burp Suite also uses a proxy. Go to Proxy -> Options and set the listener to 127.0.0.1:8080. Also, configure your browser to forward traffic to this proxy.

Crawl the Web Application: Use the Target -> Site Map feature to manually or automatically crawl the web application.

* Intercept Requests:

With Burp Suite’s Intercept feature (in the Proxy tab), you can view and modify HTTP requests before they are sent to the server.
This is useful for testing parameters, manipulating inputs, and testing the application's behavior.

* Scan for Vulnerabilities:

Burp Suite’s Scanner (in the professional version) can automatically scan for vulnerabilities, such as SQL injection and XSS.
For the free version, you can manually test for these issues using Intruder or Repeater.

# Step 5: Test for Specific Vulnerabilities

SQL Injection: Use SQLmap to check for SQL injection vulnerabilities:

* sqlmap -u "http://<target-url>/path?param=value" --dbs
  
This command tests for SQL injection on the specified parameter and retrieves databases if vulnerable.

* Cross-Site Scripting (XSS): Use Burp Suite or ZAP to manually test for XSS by inputting common payloads like <script>alert(1)</script> in input fields.

* WordPress Vulnerabilities: If the target is a WordPress site, use WPScan to look for vulnerabilities.

* wpscan --url http://<target-url> --enumerate
  
# Step 6: Analyzing and Reporting

* After scanning and testing, analyze the results for vulnerabilities.
Prioritize the issues based on severity (e.g., SQL Injection, XSS, misconfigurations).
Create a report outlining vulnerabilities, their potential impact, and recommended fixes.
