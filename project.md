# 1. DOS attack

```
`
 p  = IP(dst = "172.16.12.16")/ICMP()/"Message from dungeon"
 `
```

```
`
for i in range(10000):
    send(p)
hexdump(p)
p.show()

sendp(IP(dst="1.2.3.4",ttl=(1,4)), iface="eth0")
`
```

## More on Pinging:

```
`
    arping("192.168.169.*")

    ans,unans=sr(IP(dst="192.168.169.1-20")/ICMP())
    ans.show()
    unans.show()

    ans,unans=sr( IP(dst=”10.1.99.*”)/TCP(dport=80, flags=”S”) )

    ans,unans=sr( IP(dst="10.1.99.*"/UDP(dport=0) )
`
```

# 2. IP spoofing

```
`
p = IP(src = "192.168.169.5", dst="192.168.169.6")/ICMP()/"Hello"
`
```

# 3. NMAP using scapy (Port scanner)

```
`
    p=sr(IP(dst="192.168.169.6")/TCP(sport=666,dport=[22,80,21,443], flags="S"))

    p, v = sr(IP(dst="192.168.169.4")/TCP(sport=RandShort(), dport=[80, 22, 23, 443]), inter=0.5, retry=2, timeout=1)

    p.summary()

`
```

# 4. DNS Query:
## DNS is a UDP packet (port 53)
## rd=1  Is telling Scapy that recursion is desired

```
`

p =sr1(IP(dst="192.168.169.1")/UDP()/DNS(rd=1,qd=DNSQR(qname="www.aiktc.org")))

p.show()

sr1(IP(dst="192.168.169.1")/UDP()/DNS(rd=1,qd=DNSQR(qname="aiktc.org",qtype= "NS")))
`
```

# 5. Traceroute

```
`

traceroute(["192.168.169.6", "google.com", "aiktc.org"], dport=[80, 443],  maxttl=20)

traceroute(["192.168.169.4"], dport=22 ,maxttl=20)

ans,unans=_

ans.show()
unans.show()

`
```

# 6. Pcap:
## a) Sniffing

```
`
    a = sniff()
    a.show()
    type(a)
    len(a)
    a[0]
    a[10]


`
```
