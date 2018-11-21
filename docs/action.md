## Action
#### drop
Discards the packet, so no further processing or forwarding takes place.

#### output:port
Outputs the packet to port

#### mod_vlan_vid:vlan_vid
Modifies the VLAN id on a packet.

#### mod_vlan_pcp:vlan_pcp
Modifies the VLAN priority on a packet.

#### strip_vlan
Strips the VLAN tag from a packet if it is present.

#### push_vlan:ethertype
Push a new VLAN tag onto the packet.

#### load:value−>dst[start..end]
Writes value to bits start through end, inclusive, in field dst.
Example: load:55−>NXM_NX_REG2[0..5] loads value 55 (bit pattern 110111) into bits 0 through 5, inclusive, in register 2.