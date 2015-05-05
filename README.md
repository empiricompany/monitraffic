# monitraffic
rc.d scripting in BSD daemon trace traffic with tcpdump

Usage:
<ul>
<li>service monitraffic start</li>
<li>service monitraffic stop</li>
<li>service monitraffic status</li>
</ul>
personalize tcpdump_command in script:<br>
tcpdump_command="tcpdump -ei re2 -s 0 -G 1800 -w /var/tmp/traceLANre2-%d-%m-%Y_%H-%M-%S.pcap not port 22"


to enable it add this line on /etc/rc.conf<br>
monitraffic_enable="YES"

create crontab script to delete older .pcap files like this:<br>
\#!/bin/sh<br>
find /var/tmp/traceLANre2*.pcap -mmin +360 -delete

add to /usr/local/etc/rc.d/ to run on system boot
