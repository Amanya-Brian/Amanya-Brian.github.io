---
layout: post
title:  "The Domain Naming System (DNS)"
description: "DNS"
date:   2021-05-04 06:02:38 +0300
categories: jekyll update
---

![Workflow template](/assets/images/DNS.png)
# What is the DNS?
The simplest way of understanding the DNS is by referring to it as the *phonebook of the internet*. Web browsers interact with the internet using IP addresses, which are unique addresses of each device connected to the internet. DNS servers save humans the burden of memorizing these IP addresses by using simple domain names such as *github.com*.

## How does the DNS work?
Let's look at DNS resolution. This involves converting a user-friendly host name such as something.com into a machine-friendly address such as 192.168.3.8. These addresses ar4e called IP addresses that are given to all devices connected to the internet.
The process of DNS resolution involves many hardware components, that do not rerquire any human or browser interaction other than the request from the browser itself.
In returning an IP address for a requested page, there are DNS servers involved;
* **DNS recursor** - This receives the queries from different applications like browsers.
* **Rootname server** - This one points to more specific locations on the internet. It is the first step in resolving.
* **Top Level Domain server** - The TLD server hosts the last part of the hostname. In something.com, it hosts the *.com*. This is the next step in searching for a specific IP address.
* **Authoritative nameserver** - This is the last part in this process. If it has access to the requested resource, it will return the corresponding IP address back to the DNS recursor that made the request. 

## Through which ports is data sent to and from the server?
A DNS server uses well-known port 53 for all activities. It uses a random port above 1023 for TCP requests. A DNS client uses a random port above 1023 for its requests. This can be best summarized as below:
* A client-to-server query - source port is above 1023, destination port is 53.
* A server-to-client response - source port is 53, destination port is above 1023.
* A server-to-server query or response - at least with UDP, where both source and destination port are 53; with TCP, the requesting server will use a port above 1023.

## How are host names mapped to IP addresses?
These configurations are stored in zone files. Zone files contain information about a namespace. This information is categorized into *directives* and *resource records*. Zone file directives are optional but the resource records are key in order to give identities to individual host names. 
Zone file directives include *$INCLUDE* which allows additional zone settings to be stored other than the main zone file ,*$ORIGIN* which appends a domain name to records with a host name and nothing more and *$TTL* which sets the default Time To Live for the zone resource record, the time for which it is valid.
### Resource Records(DNS Records)
Resource records are the primary components of a zone file. The most frequently used zone files include;
* **A** - This refers to the Address record, which specifies an IP address to assign to a name.
{% highlight ruby %}
<host>	IN	A	<IP-address>
{% endhighlight %}

* **CNAME** - This is the cannonical name record which maps one name to another. It is also sometimes called the alias record. In this example, an **A** record binds a hostname to an IP address, while a CNAME record points the commonly used www hostname to it.
{% highlight ruby %}
server1	IN	A	10.0.1.5 
www	IN	CNAME	server1
{% endhighlight %}

* **MX** - This is the Mail eXchange record, which tells where mail sent to a particular namespace controlled by this zone should go. In this example, <preference-value> allows numerical ranking of the email servers for a namespace, giving preference to some email systems over others. The MX resource record with the lowest <preference-value> is preferred over the others. However, multiple email servers can possess the same value to distribute email traffic evenly among them.
{% highlight ruby %}
IN	MX	<preference-value>	<email-server-name>

    IN     MX     10     mail.example.com.       
	IN     MX     20     mail2.example.com.
{% endhighlight %}
In this example, the mail.example.com email server is preferred to the mail2.example.com email server when receiving email destined for the example.com domain.

* **NS** - This is the nameserver record, which announces the authoritative namservers for a particular zone. Here is how it can be used;
{% highlight ruby %}
    IN     NS     <nameserver-name>
{% endhighlight %}

* **SOA** - This refers to the Start Of Authority resource record, which specifies important authoritative information about a namespace to the nameserver. It is the  first resource record in a zone file. This is the basic structure of an SOA file;
{% highlight ruby %}
@     IN     SOA    <primary-name-server>	<hostmaster-email> (
	<serial-number>
	<time-to-refresh>
	<time-to-retry>
	<time-to-expire>
	<minimum-TTL> )
{% endhighlight %}
The @ symbol places the $ORIGIN directive (or the zone's name, if the $ORIGIN directive is not set) as the namespace being defined by this SOA resource record. The hostname of the primary nameserver that is authoritative for this domain is the <primary-name-server> directive, and the email of the person to contact about this namespace is the <hostmaster-email> directive.

The <serial-number> directive is a numerical value incremented every time the zone file is altered to indicate it is time for named to reload the zone. The <time-to-refresh> directive is the numerical value slave servers use to determine how long to wait before asking the master nameserver if any changes have been made to the zone. The <serial-number> directive is a numerical value used by the slave servers to determine if it is using outdated zone data and should therefore refresh it.

The <time-to-retry> directive is a numerical value used by slave servers to determine the length of time to wait before issuing a refresh request in the event that the master nameserver is not answering. If the master has not replied to a refresh request before the amount of time specified in the <time-to-expire> directive elapses, the slave servers stop responding as an authority for requests concerning that namespace.

The <minimum-TTL> directive is the amount of time other nameservers cache the zone's information. 

## Example zone file
This is an example of a very basic zone file.
{% highlight ruby %}
$ORIGIN example.com. 
$TTL 86400 
@	IN	SOA	dns1.example.com.	hostmaster.example.com. (
			2001062501 ; serial                     
			21600      ; refresh after 6 hours                     
			3600       ; retry after 1 hour                     
			604800     ; expire after 1 week                     
			86400 )    ; minimum TTL of 1 day  
		     
		           
	IN	NS	dns1.example.com.       
	IN	NS	dns2.example.com.        
	
	
	IN	MX	10	mail.example.com.       
	IN	MX	20	mail2.example.com.        

	
dns1	IN	A	10.0.1.1
dns2	IN	A	10.0.1.2	

			       
server1	IN	A	10.0.1.5        
server2	IN	A	10.0.1.6

       
ftp	IN	A	10.0.1.3
	IN	A	10.0.1.4
	
mail	IN	CNAME	server1
mail2	IN	CNAME	server2


www	IN	CNAME	server1
{% endhighlight %}

## Popular DNS servers
BIND or named (pronounced name-dee, short for name daemon), is an implementation of the Domain Name System (DNS) of the Internet. It performs both of the main DNS server roles, acting as an authoritative name server for domains, and acting as a recursive resolver in the network. 