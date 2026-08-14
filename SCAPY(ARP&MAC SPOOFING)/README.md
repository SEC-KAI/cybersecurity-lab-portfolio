In this lab, I used scapy to create packets to perform arp and mac spoofing.

1. First I tried out pinging targets with scapy by creating an ip packet that uses icmp protocol.
   COMMAND:
   packet = IP(dst="target_ip")/ICMP()
     This sends an ip packet with the destination of the target ip, using the ICMP protocol and stores it in the "packet" variable
   result = sr1(packet, timeout=1)
     This sends and recieves 1 packet with timeout=1 and stores it in the "result" variable.
   
2. I then created packets that would scan ports on a device
   COMMAND:
   packet = IP(dst="target_ip")/TCP(dport=(1,100),flags="S")
     This sends an ip packet using tcp protocol and scans ports 1-100 using syn flag
   ans, unans = sr(packet, timeout=1)
     This sends and recieves packets from the "packet" process and stores the answered and unanswered ports in the variable
   
3. I also made a packet that would give me the mac address of a device by creating an ARP packet.
   COMMAND:
   packet = ARP(pdst="target_ip")
     This sends an ARP request to the target ip
   result = sr1(packet, timeout=3)
     This sends and recieves 1 packet from the "packet" process and stores it in the result variable
   
4. lastly, I modified the ARP packet to spoof the source ip.
   COMMAND:
   packet = ARP(pdst="target_ip",psrc="spoofed_ip")
   
5. Additionally, I monitored the traffic and found out that traffic from target to router can be seen from the attacker device
   since the traffic gets forwarded to the attacker's mac address.
