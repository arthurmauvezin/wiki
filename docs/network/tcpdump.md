# tcpdump

## Basic scan
Scan without translating hostnames and ports, with full verbosity, on any interfaces, writing output to file_name.pcap
```bash
tcpdump -nvvv -i any -w <file_name>.pcap
```

## Filters
### Scan filtering host hostname
Scan capturing 3 packets
```bash
tcpdump -nvvv -i any -c 3 host <hostname>
```

### Userful filters
```bash
src <ip>
port <port_number>
```

### Filters operator
All filters [here](http://www.tcpdump.org/manpages/pcap-filter.7.html)
```bash
and 
or
```

### Usage
```bash
tcpdump -nvvv -i any '<filters>'
```

### Examples
```bash
src host 10.0.3.1
port 22 and port 60738
port 22 && port 60738
port 80 or port 443
(port 80 or port 443) and host 10.0.3.169
((port 80 or port 443) and (host 10.0.3.169 or host 10.0.3.1)) and dst host 10.0.3.246
```

## Output
```bash
10.0.3.246.56894 > 192.168.0.92.22: Flags [S], cksum 0xcf28 (incorrect -> 0x0388), seq 682725222, win 29200, options [mss 1460,sackOK,TS val 619989005 ecr 0,nop,wscale 7], length 0
     (1)                 (2)	      (3)
```
### (1) src-ip.src-port
### (2) dst-ip.dst-port
### (3) type of packet
There are many types of packet. 

* [S] - SYN (Start connection)
* [.] - No Flag Set
* [P] - PSH (Push data)
* [F] - FIN (Finish connection)
* [R] - RST (Reset connection)
* [S.] - SYN-ACK packet

## Packet Inspection
### Print packet data in Hex and ASCII : -XX
```bash
tcpdump -nvvv -i any -c 1 -XX 'port 80 and host 10.0.3.1'
```

### Print packet data in ASCII only : -A
```bash
tcpdump -nvvv -i any -c 1 -A 'port 80 and host 10.0.3.1'
```

## Non-TCP Traffic
### ICMP packets
```bash
tcpdump -nvvv -i any -c 2 icmp
```

### UDP packets
```bash
tcpdump -nvvv -i any -c 2 udp
```
