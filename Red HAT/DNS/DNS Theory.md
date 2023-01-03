# <font size=7> <span style="color: green">DNS (Domain Name System) </font></span>

<font size=4>A DNS server is a type of computer server that is responsible for resolving domain names to their corresponding IP addresses. This is an essential function that allows users to access websites and other online resources using human-readable names, rather than having to remember the numerical IP addresses of the servers that host those resources. When a user types a domain name into their web browser, the DNS server translates that name into the corresponding IP address and directs the user's browser to the correct website.</font>

# <font size=5><span style="color:red">Type of DNS</span></font>
**1. Primary DNS**
			
A primary DNS server is a server that stores the authoritative records for a domain. It is the first server that is queried when a client needs to resolve a domain name to an IP address. The primary DNS server is responsible for providing the correct IP address for a given domain name. If the primary DNS server cannot resolve the domain name, it will usually forward the request to a secondary DNS server.

**2. Secondery DNS**
			
Secondary DNS, also known as a secondary Domain Name System, is a type of DNS server that acts as a backup for the primary DNS server.

**3. Cache DNS**

Caching DNS is a system for storing DNS query results in a cache, so that future queries for the same domain name can be resolved faster. This helps improve the speed and performance of the DNS system, as it reduces the need for repeated DNS queries to the same server. When a DNS query is made, the caching DNS server will check its cache to see if it has a recent and valid result for the query. If it does, it will return the cached result to the user, which is faster than having to send the query to a remote DNS server and wait for a response. This can be especially beneficial when dealing with large numbers of DNS queries, as it can help reduce the load on the DNS system and improve overall performance.

**4. Forward DNS**

Forward DNS (Domain Name System) is a process that translates human-readable domain names into numerical IP addresses that computers can use to communicate with each other. This is also known as "forward resolution". When you enter a domain name into your web browser, your computer sends a request to a DNS server to look up the corresponding IP address for that domain. The DNS server then responds with the IP address, which your computer uses to establish a connection to the website's server. Forward DNS is an essential part of the internet's infrastructure, as it allows us to use easily-remembered domain names instead of long strings of numbers to access websites and other online resources.

# Type of DNS Record

**<font size=5> A Redcord** </font>

When you type a domain name into a web browser, the A record is used to translate the domain name into an IPv4 address, which the computer uses to connect to the correct website.

**<font size=5> AAAA Redcord** </font>

When you type a domain name into a web browser, the AAAA record is used to translate the domain name into an IPv6 address, which the computer uses to connect to the correct website.	

**<font size=5> MX Redcord** </font>

When someone sends an email to a domain, the sending mail server looks up the MX record for that domain to determine the correct mail server to send the message to.

**<font size=5> NS Redcord** </font>

When you register a domain name, you typically need to specify the name servers that will be responsible for the domain. This is done by creating NS records for the domain that point to the name servers.

**<font size=5> CNAME Redcord** </font>

A CNAME record can be used to redirect traffic from one domain name to another. This can be useful if you want to use a shorter or more memorable domain name to access a website, but the actual website is hosted on a different domain.

**<font size=5> SOA Redcord** </font>

The SOA record specifies the domain name of the primary DNS server for a domain. This server is responsible for managing and updating the DNS records for the domain.

**<font size=5> PTR Redcord** </font>

PTR records can be used to identify the owner of an IP address, which can be useful for tracking down sources of spam or other malicious activity.
