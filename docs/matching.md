## Matching Fields
1. port
in_port=port

Matches OpenFlow port port

2. VLAN
dl_vlan=vlan

Matches IEEE 802.1q Virtual LAN tag vlan.

3. VLAN pcp
dl_vlan_pcp=priority

Matches IEEE 802.1q Priority Code Point (PCP) priority, which is specified as a value between 0 and 7, inclusive. A higher value indicates a higher frame priority level.

4. MAC Address
dl_src=xx:xx:xx:xx:xx:xx
dl_dst=xx:xx:xx:xx:xx:xx

Matches an Ethernet source (or destination) address specified as 6 pairs of hexadecimal digits delimited by colons (e.g. 00:0A:E4:25:6B:B0).

5. MAC Address + Wildcard
dl_src=xx:xx:xx:xx:xx:xx/xx:xx:xx:xx:xx:xx
dl_dst=xx:xx:xx:xx:xx:xx/xx:xx:xx:xx:xx:xx

Matches an Ethernet destination address specified as 6 pairs of hexadecimal digits delimited by colons (e.g. 00:0A:E4:25:6B:B0), with a wildcard mask following the slash.

01:00:00:00:00:00 Match only the multicast bit. Thus, dl_dst=01:00:00:00:00:00/01:00:00:00:00:00 matches all multicast (including broadcast) Ethernet packets, and dl_dst=00:00:00:00:00:00/01:00:00:00:00:00 matches all unicast Ethernet packets.

ff:ff:ff:ff:ff:ff Exact match (equivalent to omitting the mask).

00:00:00:00:00:00 Wildcard all bits (equivalent to dl_dst=* ).

6. Ether Type
dl_type=ethertype
Matches Ethernet protocol type ethertype, which is specified as an integer between 0 and 65535

7. IP Address
nw_src=ip[/netmask]
nw_dst=ip[/netmask]
When dl_type is 0x0800 (possibly via shorthand, e.g. ip or tcp), matches IPv4 source (or destination) address ip, which may be specified as an IP address or host name

When dl_type=0x0806 or arp is specified, matches the ar_spa or ar_tpa field, respectively, in ARP packets for IPv4 and Ethernet.

When dl_type=0x8035 or rarp is specified, matches the ar_spa or ar_tpa field, respectively, in RARP packets for IPv4 and Ethernet.

8. Proto
nw_proto=proto
When ip or dl_type=0x0800 is specified, matches IP protocol type proto, which is specified as a decimal number between 0 and 255, inclusive (e.g. 1 to match ICMP packets or 6 to match TCP packets).

When ipv6 or dl_type=0x86dd is specified, matches IPv6 header type proto, which is specified as a decimal number between 0 and 255, inclusive (e.g. 58 to match ICMPv6 packets or 6 to match TCP).

When arp or dl_type=0x0806 is specified, matches the lower 8 bits of the ARP opcode.

When rarp or dl_type=0x8035 is specified, matches the lower 8 bits of the ARP opcode.

9. TOS
nw_tos=tos
Matches IP ToS/DSCP or IPv6 traffic class field tos, which is specified as a decimal number between 0 and 255, inclusive.

10. ECN
nw_ecn=ecn
Matches ecn bits in IP ToS or IPv6 traffic class fields, which is specified as a decimal number between 0 and 3, inclusive.

11. TTL
nw_ttl=ttl
Matches IP TTL or IPv6 hop limit value ttl, which is specified as a decimal number between 0 and 255, inclusive.

12. TCP/UDP SRC/DST Port
tp_src=port
tp_dst=port
When dl_type and nw_proto specify TCP or UDP, tp_src and tp_dst match the UDP or TCP source or destination port port

13. ICMP
icmp_type=type
icmp_code=code
When dl_type and nw_proto specify ICMP or ICMPv6, type matches the ICMP type and code matches the ICMP code.

14. Flow Table
table=number
If specified, limits the flow manipulation and flow dump commands to only apply to the table with the given number between 0 and 254.

15. VLAN Tagging
vlan_tci=tci[/mask]

Matches modified VLAN TCI tci. If mask is omitted, tci is the exact VLAN TCI to match; if mask is specified, then a 1-bit in mask indicates that the corresponding bit in tci must match exactly, and a 0-bit wildcards that bit.

16. IP Fragment
ip_frag=frag_type

When dl_type specifies IP or IPv6, frag_type specifies what kind of IP fragments or non-fragments to match.

The following values of frag_type are supported:

no Matches only non-fragmented packets.
yes Matches all fragments.
first Matches only fragments with offset 0.
later Matches only fragments with nonzero offset.
not_later Matches non-fragmented packets and fragments with zero offset.

17. ARP
arp_sha=xx:xx:xx:xx:xx:xx
arp_tha=xx:xx:xx:xx:xx:xx

When dl_type specifies either ARP or RARP, arp_sha and arp_tha match the source and target hardware address, respectively.

18. Tunnel ID
tun_id=tunnel-id[/mask]

Matches tunnel identifier tunnel-id. Only packets that arrive over a tunnel that carries a key (e.g. GRE with the RFC 2890 key extension and a nonzero key value) will have a nonzero tunnel ID.