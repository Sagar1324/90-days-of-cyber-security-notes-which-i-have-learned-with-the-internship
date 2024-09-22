# BURIP SUITE:

Burp Suite is a comprehensive tool for web application security testing. It is widely used by security professionals and penetration testers to identify vulnerabilities in web applications. Developed by PortSwigger, Burp Suite offers both a free (Community) version and a paid (Professional) version, with the latter offering more advanced features.

# Using Burp Suite:

1. Setting Up Proxy:

To use Burp Suite, you need to configure your browser to send traffic through Burp’s proxy. Here’s how to set it up:

By default, Burp Suite listens on 127.0.0.1:8080.
In your browser, set up the proxy to forward all traffic through 127.0.0.1:8080.
Alternatively, you can use the Burp Suite Browser, which comes pre-configured to work with Burp, eliminating the need to manually set up a proxy.

2. Intercepting and Modifying Requests:

Once Burp Suite is set up as a proxy, you can intercept all HTTP/S requests.
You can enable Intercept in the Proxy tab to pause requests and manually edit or drop them before they reach the web server.
For example, you can change a request parameter to test for injection attacks or replay a modified request to see how the server responds.

3. Scanning for Vulnerabilities:
(Professional Version)

After intercepting and exploring the web application, you can use the Scanner to automatically scan for vulnerabilities.
Right-click on any URL or folder in the Site Map and select "Scan" to perform a scan of the web application.
The results will be displayed in the Issues tab, which categorizes vulnerabilities by severity and provides information on how to address them.

4. Fuzzing with Intruder:
You can send requests to Intruder to fuzz parameters such as URL parameters, headers, or even cookies.
Define attack positions, insert payloads (e.g., lists of common passwords or malicious inputs), and let Intruder perform the test.
It will give you a detailed response to each payload, helping you identify security flaws like weak password policies or unsanitized inputs.
Editions of Burp Suite

# Common Use Cases:

* Manual Web App Testing:

Burp Suite allows for detailed manual testing by intercepting and modifying web requests to test for vulnerabilities such as SQL injection, XSS, and authentication flaws.

* Automated Vulnerability Scanning (Pro Version):

The Scanner automates vulnerability detection, which helps you quickly identify common security issues without manual effort.

* Brute-Force and Fuzzing:

The Intruder tool is ideal for testing web application inputs, such as login forms, by brute-forcing or fuzzing.

* Session Management:

By analyzing cookies, session tokens, and other authentication mechanisms, Burp Suite can help you determine if they are secure or vulnerable to attacks like session fixation or session hijacking.




# Step-by-Step Guide to Perform Brute Force Attack

# 1. Start and Configure DVWA

If you haven't set up DVWA, follow these steps:

* DVWA should be running on your localhost (typically at http://localhost/dvwa or http://127.0.0.1/dvwa).

* Open DVWA in your browser and log in with the default credentials (admin:password).
After logging in:

* Navigate to the DVWA Security page and set the security level to Low or Medium to allow brute-forcing.

*Ensure that the web server (Apache) and database (MySQL) are up and running.

# 2. Open Burp Suite in Kali Linux

Launch Burp Suite from Kali Linux by typing:

* burpsuite

* On the startup screen, choose Temporary Project and click Next.

* Click Start Burp to open the main interface.

# 3. Configure Browser Proxy for Burp Suite

You need to intercept traffic between your browser and the target application (DVWA).

* In Burp Suite, go to the Proxy tab, and then the Intercept sub-tab.

* By default, Burp Suite listens on 127.0.0.1:8080. Set your browser to forward traffic through this proxy.

* In Firefox (or any browser you're using):

  * Open the browser’s settings, navigate to Network Settings, and configure the proxy as follows:
  * HTTP Proxy: 127.0.0.1
  * Port: 8080
* Ensure all traffic is routed through Burp Suite by this proxy.
  
# 4. Access DVWA and Intercept Login Request

* Open your browser and go to http://localhost/dvwa/login.php.
* Enter incorrect credentials (any random username and password) and attempt to log in.
* Burp Suite will intercept the request.

In Burp Suite:

* In the Proxy tab, go to Intercept.
* You’ll see the login POST request intercepted by Burp.
  
# 5. Send the Request to Intruder

Now, we will send this intercepted login request to Intruder for brute-forcing.

* In the Intercept tab, right-click on the intercepted request and select Send to Intruder.

# 6. Configure Intruder Attack Positions

1. Go to the Intruder tab.
2. Select Positions.
In this step, we will mark the positions we want to brute-force (i.e., the username and password fields).

* You’ll see the entire HTTP request. Burp Suite will automatically add positions for the parameters, but we will modify these.

* Highlight the username and password values in the request, and click Add § to mark them as positions for the attack. Example:

  * POST /dvwa/login.php HTTP/1.1
  * Host: localhost
  * User-Agent: Mozilla/5.0 ...
  * Content-Type: application/x-www-form-urlencoded
  * Content-Length: 50
  * username=§admin§&password=§password§&Login=Login

Ensure only the username and password parameters are marked (with § symbols around them).

#  7. Select Payloads

1. Go to the Payloads tab.

2. Set Payload Set 1 for the username.

  * You can either use a list of common usernames (e.g., admin, test, user) or use the default username admin.
  * If you are attacking a single user, use a single payload like admin.
3.For Payload Set 2 (password field):

  * Load a list of common passwords or create your own password list.
  * You can use Kali Linux's built-in wordlists located at /usr/share/wordlists/rockyou.txt (make sure it's unzipped).
Example command to unzip and locate it:

* gunzip /usr/share/wordlists/rockyou.txt.gz
  
Then, you can load this file as your password list.

# 8. Start the Attack

* Once you’ve configured the payloads, click Start Attack.
* Burp Suite will begin testing the combinations of usernames and passwords from your list.

# 9. Monitor the Results

During the attack:

* Burp Suite will show the status of each login attempt in a new window.

* Look for the Length column or Status codes (HTTP 200 vs 302). When a successful login is found, the response length will differ from failed attempts, or the status code may indicate a redirection (302) to another page, such as a successful login redirect.

* Burp Suite will highlight the successful login attempt with different lengths or status codes (depending on the behavior of the login page).

# 10. Verify the Credentials

After the attack finishes:

  * Identify the correct username and password combination based on the different response length or status code.
  * Log in to DVWA with the found credentials to verify the success of the brute force attack.

















