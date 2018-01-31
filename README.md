![Logo](logo.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2018-01-31)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.38.14.171|tor-exit.r2.apx.pub|9
171.25.193.20|tor-exit0-readme.dfri.se|9
171.25.193.25|tor-exit5-readme.dfri.se|9
176.10.99.200|-|9
188.166.158.162|-|9
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|9
78.84.194.34|-|8
176.10.104.240|tor1e1.digitale-gesellschaft.ch|8
218.156.85.17|-|8
113.108.72.2|-|8
202.137.147.108|ns1.mof.gov.la|8
78.109.23.1|tornode.torreactor.ml|8
104.223.123.98|unassigned.quadranet.com|8
197.231.221.211|exit1.ipredator.se|8
23.129.64.102|xanaduregio.emeraldonion.org|8
5.196.1.129|tor.thd.ninja|8
80.67.172.162|algrothendieck.nos-oignons.net|8
23.110.54.178|-|8
171.25.193.77|tor-exit1-readme.dfri.se|8
171.25.193.78|tor-exit4-readme.dfri.se|8
5.9.158.75|tor-relay.zwiebeltoralf.de|8
190.248.144.42|cable190-248-144-42.une.net.co|8
80.82.77.139|dojo.census.shodan.io|8
180.96.14.234|-|8
50.62.139.155|ip-50-62-139-155.ip.secureserver.net|8
173.254.216.66|exit-01a.noisetor.net|8
192.160.102.170|ogopogo.relay.coldhak.com|8
8.26.21.39|39.21.26.8.serverpronto.com|8
104.245.93.25|-|8
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|8
185.94.111.1|-|8
66.70.217.179|tor.cusse.org|8
118.186.36.50|-|8
