# Keep-Digging

Simple network abuse check guide on Linux

The pre-designed version of Linux that has most of the programs and features already installed, its Kali Linux. Otherwise, if you go with the general Debian or Ubuntu install, you can make your environment friendly and efficient to analyze network traffic and explore possible intruders on the Internet Service Provider router. 

Install:
1. Wireshark (to capture traffic on any network device)
2. sysdig (checks for root processes being run on the network connections)
3. nmap (scans IP addresses for open ports)

Before enabling an internet connection, start to record a terminal session. Enabling terminal recording is simple, just type: script /location/fileName.log (type exit once you are done recording)
When connected:
1. obtain IP info: sudo ifconfig
2. check root connections on ipv4 and ipv6 wih sysdig:
sudo sysdig -c lsof "'fd.type=ipv4 and user.name=root'"
sudo sysdig -c lsof "'fd.type=ipv6 and user.name=root'"
3. check how the proces is connected to the program hierarchy:
pstree -p -s PIDnumber
4. check where connections get established and from which processes: lsof -i
(with killing previous root processes, the number of connections diminish when lsof -i is run). 
5. check /etc/services and compare them with the default file that came with your original installation
cat /etc/services
6. check iptables for any set rules on forewarding and accept policy. If rules are set, flush them.
7. check for open ports on your gataway: nmap -v -A gataway or IP used as your outgoing address. 

Guide will be updated accordingly and never believe an IT person when they say to do a reinstall without checking for yourself the current state and possible presence of keyllogers and other malicious software.

Keep digging, to make informed decisions!
