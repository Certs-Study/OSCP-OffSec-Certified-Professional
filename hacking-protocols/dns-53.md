# DNS - 53

### DNS Enumeration

DNS Enumeration is a process used in network security to gather information about Domain Name Systems (DNS) to identify network infrastructure vulnerabilities, configurations, and potential avenues for cyber attacks. It involves querying DNS servers to uncover valuable details about hostnames, IP addresses of networked devices, and other domain-related information.&#x20;

This process is crucial for ethical hackers and security professionals to understand the target environment, identify potential security flaws, and enhance network security by addressing discovered issues.&#x20;

DNS Enumeration can be performed using various tools and techniques, both manually and automatically, to systematically collect and analyze DNS records and settings.

#### Tools Used in DNS Enumeration

Various tools have been developed to facilitate DNS Enumeration, each offering unique features to assist in uncovering DNS and networking information. Here are some commonly used tools:

* **Nmap**: Widely known for network discovery and security auditing, Nmap can also perform DNS Enumeration to identify hosts in a network.
* **DNSrecon**: A powerful Python script specifically designed for DNS Enumeration, providing a wide range of functionalities including DNS record enumeration and zone transfer tests.
* **Fierce**: A Perl script that quickly scans domains for DNS information, helping identify valuable targets and potential vulnerabilities.
* **TheHarvester**: A tool designed for gathering e-mail accounts, subdomain names, virtual hosts, and more from different public sources (search engines, social networks) which can include DNS-related information.

#### Techniques in DNS Enumeration

DNS Enumeration encompasses a variety of techniques to extract detailed information about target networks. Key techniques include:

* **Zone Transfers**: Attempting to get a copy of the zone data from a DNS server. Successful zone transfers can reveal detailed information about every device in the network.
* **Reverse DNS Lookups**: Mapping IP addresses back to hostnames, can help in identifying various servers and devices.
* **DNS Record Enumeration**: Collecting data on various DNS records (A, AAAA, MX, NS, SOA, TXT) which can reveal information about domain names, mail servers, and other network infrastructure components.

### **DNS Hacking Use Case**

DNS hacking can involve various malicious activities aimed at exploiting vulnerabilities within the DNS.&#x20;

A common use case of DNS hacking is DNS Spoofing (or DNS Cache Poisoning), where an attacker intercepts and alters DNS queries to redirect traffic from legitimate servers to malicious ones.&#x20;

This can lead to man-in-the-middle attacks, phishing schemes, or the spread of malware.&#x20;

Understanding DNS Enumeration techniques not only helps in identifying such vulnerabilities but also aids in creating strategies to mitigate potential DNS-based attacks.

**Mitigating DNS Vulnerabilities**

Mitigating DNS vulnerabilities requires a comprehensive approach involving several strategies:

* **Regular Audits**: Conduct regular audits and assessments of DNS configurations and records to identify potential vulnerabilities or misconfigurations.
* **DNSSEC**: Implement DNS Security Extensions (DNSSEC) to protect against DNS spoofing by ensuring that DNS queries and responses are authenticated and verified.
* **Access Control**: Restrict zone transfers to only authorized DNS servers to prevent unauthorized access to DNS records.
* **Monitoring and Alerting**: Implement monitoring and alerting systems to detect unusual DNS requests or unexpected changes in DNS records, which could indicate a potential attack.

### DNS Zone Transfer

#### DNS Zone Transfer Attack Vector

DNS Zone Transfer attacks exploit vulnerabilities in the DNS server configuration, allowing attackers to replicate the entire DNS record database of a target domain. This can provide the attacker with critical information about the internal network structure, including the details of all the domain's subdomains and associated IP addresses.

```
$ dig zonetransfer.me ns +short 

nsztm2.digi.ninja.
nsztm1.digi.ninja.

$ dig axfr zonetransfer.me @nsztm1.digi.ninja

; <<>> DiG 9.16.18 <<>> axfr zonetransfer.me @nsztm1.digi.ninja
;; global options: +cmd
zonetransfer.me.    7200    IN  SOA nsztm1.digi.ninja. robin.digi.ninja. 2019100801 172800 900 1209600 3600
zonetransfer.me.    300 IN  HINFO   "Casio fx-700G" "Windows XP"
zonetransfer.me.    301 IN  TXT "google-site-verification=tyP28J7JAUHA9fw2sHXMgcCC0I6XBmmoVi04VlMewxA"
zonetransfer.me.    7200    IN  MX  0 ASPMX.L.GOOGLE.COM.
zonetransfer.me.    7200    IN  MX  10 ALT1.ASPMX.L.GOOGLE.COM.
zonetransfer.me.    7200    IN  MX  10 ALT2.ASPMX.L.GOOGLE.COM.
zonetransfer.me.    7200    IN  MX  20 ASPMX2.GOOGLEMAIL.COM.
zonetransfer.me.    7200    IN  MX  20 ASPMX3.GOOGLEMAIL.COM.
zonetransfer.me.    7200    IN  MX  20 ASPMX4.GOOGLEMAIL.COM.
zonetransfer.me.    7200    IN  MX  20 ASPMX5.GOOGLEMAIL.COM.
zonetransfer.me.    7200    IN  A   5.196.105.14
zonetransfer.me.    7200    IN  NS  nsztm1.digi.ninja.
zonetransfer.me.    7200    IN  NS  nsztm2.digi.ninja.
_acme-challenge.zonetransfer.me. 301 IN TXT "6Oa05hbUJ9xSsvYy7pApQvwCUSSGgxvrbdizjePEsZI"
_sip._tcp.zonetransfer.me. 14000 IN SRV 0 0 5060 www.zonetransfer.me.
14.105.196.5.IN-ADDR.ARPA.zonetransfer.me. 7200 IN PTR www.zonetransfer.me.
asfdbauthdns.zonetransfer.me. 7900 IN   AFSDB   1 asfdbbox.zonetransfer.me.
asfdbbox.zonetransfer.me. 7200  IN  A   127.0.0.1
asfdbvolume.zonetransfer.me. 7800 IN    AFSDB   1 asfdbbox.zonetransfer.me.
canberra-office.zonetransfer.me. 7200 IN A  202.14.81.230
cmdexec.zonetransfer.me. 300    IN  TXT "; ls"
contact.zonetransfer.me. 2592000 IN TXT "Remember to call or email Pippa on +44 123 4567890 or pippa@zonetransfer.me when making DNS changes"
dc-office.zonetransfer.me. 7200 IN  A   143.228.181.132
deadbeef.zonetransfer.me. 7201  IN  AAAA    dead:beaf::
dr.zonetransfer.me. 300 IN  LOC 53 20 56.558 N 1 38 33.526 W 0.00m 1m 10000m 10m
DZC.zonetransfer.me.    7200    IN  TXT "AbCdEfG"
email.zonetransfer.me.  2222    IN  NAPTR   1 1 "P" "E2U+email" "" email.zonetransfer.me.zonetransfer.me.
email.zonetransfer.me.  7200    IN  A   74.125.206.26
Hello.zonetransfer.me.  7200    IN  TXT "Hi to Josh and all his class"
home.zonetransfer.me.   7200    IN  A   127.0.0.1
Info.zonetransfer.me.   7200    IN  TXT "ZoneTransfer.me service provided by Robin Wood - robin@digi.ninja. See http://digi.ninja/projects/zonetransferme.php for more information."
internal.zonetransfer.me. 300   IN  NS  intns1.zonetransfer.me.
internal.zonetransfer.me. 300   IN  NS  intns2.zonetransfer.me.
intns1.zonetransfer.me. 300 IN  A   81.4.108.41
intns2.zonetransfer.me. 300 IN  A   167.88.42.94
office.zonetransfer.me. 7200    IN  A   4.23.39.254
ipv6actnow.org.zonetransfer.me. 7200 IN AAAA    2001:67c:2e8:11::c100:1332
owa.zonetransfer.me.    7200    IN  A   207.46.197.32
robinwood.zonetransfer.me. 302  IN  TXT "Robin Wood"
rp.zonetransfer.me. 321 IN  RP  robin.zonetransfer.me. robinwood.zonetransfer.me.
sip.zonetransfer.me.    3333    IN  NAPTR   2 3 "P" "E2U+sip" "!^.*$!sip:customer-service@zonetransfer.me!" .
sqli.zonetransfer.me.   300 IN  TXT "' or 1=1 --"
sshock.zonetransfer.me. 7200    IN  TXT "() { :]}; echo ShellShocked"
staging.zonetransfer.me. 7200   IN  CNAME   www.sydneyoperahouse.com.
alltcpportsopen.firewall.test.zonetransfer.me. 301 IN A 127.0.0.1
testing.zonetransfer.me. 301    IN  CNAME   www.zonetransfer.me.
vpn.zonetransfer.me.    4000    IN  A   174.36.59.154
www.zonetransfer.me.    7200    IN  A   5.196.105.14
xss.zonetransfer.me.    300 IN  TXT "'><script>alert('Boo')</script>"
zonetransfer.me.    7200    IN  SOA nsztm1.digi.ninja. robin.digi.ninja. 2019100801 172800 900 1209600 3600
;; Query time: 133 msec
;; SERVER: 81.4.108.41#53(81.4.108.41)
;; WHEN: Thu Jul 22 17:28:02 IST 2021
;; XFR size: 50 records (messages 1, bytes 1994)
```

## Sub-Domain Enumeration

```
sublist3r -d <domain>
# To scan with public data

sublist3r -d <domain> -b -t 100
# To bruteforce the subdomains
# this will use following wordlist:
    /usr/share/sublist3r/subbrute/names.txt
```
