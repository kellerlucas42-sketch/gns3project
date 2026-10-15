# gns3project
GNS3 Project

# Lucas Keller - GNS3 Networking 

## Purpose

The purpose of static routes is to manually direct network traffic along a chosen path. They are useful when an administrator wants predictable routing. If IP addresses or network layouts change often, static routes can require more manual updates.

## What can happen if a static route is misconfigured?

A misconfigured static route, such as one with the wrong next-hop IP address, can cause traffic to fail to reach its destination or take an unintended path. A next hop that is not reachable through a directly connected network may prevent the route from being installed in the routing table. Incorrect routes can also contribute to routing loops.

## How can you verify a static route?

Use `show ip route` on the router and check that the expected route appears with an `S` entry and the correct destination network, mask or prefix length, and next hop. You can also ping the next hop and destination. To test end-to-end connectivity and return paths, ping from a host in the appropriate VLAN on a non-distribution switch.

## How does traceroute help verify the route?

The `traceroute` command shows the hops a packet takes toward its destination. Comparing the reported hops with the intended topology helps confirm whether traffic is following the expected path. A hop that does not respond may be filtering or not returning traceroute probes, so a missing response does not always prove that forwarding has failed.

## Why do routers return ICMP messages for the initial probe packets?

Each router decreases the packet's Time to Live (TTL) by one as it forwards the packet. When a router receives a packet whose TTL expires, it discards the packet and normally sends an ICMP *Time Exceeded* message to the source. Traceroute intentionally sends probes with increasing TTL values so each successive router can identify itself. The probes are not forwarded after their TTL expires.

## Screenshots

Add the screenshots in the following order. Replace each placeholder with the relevant image filename or a Markdown image link.

1. **PC1 IP configuration and connectivity tests** — PC1 showing its IP configuration and pings to PC4, PC5, and PC8.
2. **Network topology** — the GNS3 topology for the lab.
3. **R1 routing table** — output of `show ip route` on R1.
4. **R2 routing table** — output of `show ip route` on R2.
5. **Switch interface status** — `show interfaces status` output.
6. **Switch trunk configuration** — `show interfaces trunk` output.
7. **Spanning Tree summary** — `show spanning-tree summary` output.
8. **ESW-ODD routing table** — output of `show ip route` on ESW-ODD.
9. **ESW-EVEN routing table** — output of `show ip route` on ESW-EVEN.
10. **Wireshark capture, TTL 1** — probe packet showing TTL 1 and the corresponding ICMP response.
11. **Wireshark capture, TTL 3** — probe packet showing TTL 3 and the corresponding ICMP response.
12. **Wireshark capture, TTL 5** — probe packet showing TTL 5 and the corresponding ICMP response.

### Screenshot placeholders

If the images are stored alongside this Markdown file, you can use this format and update each filename:

```markdown
![PC1 IP configuration and pings](screenshots/01-pc1-ip-and-pings.png)
![GNS3 network topology](screenshots/02-network-topology.png)
![R1 routing table](screenshots/03-r1-show-ip-route.png)
![R2 routing table](screenshots/04-r2-show-ip-route.png)
![Switch interface status](screenshots/05-interface-status.png)
![Switch trunk status](screenshots/06-interface-trunk.png)
![Spanning Tree summary](screenshots/07-stp-summary.png)
![ESW-ODD routing table](screenshots/08-esw-odd-show-ip-route.png)
![ESW-EVEN routing table](images/Screenshot%202026-10-06%20132656.png)
![Wireshark TTL 1](screenshots/10-wireshark-ttl-1.png)
![Wireshark TTL 3](screenshots/11-wireshark-ttl-3.png)
![Wireshark TTL 5](screenshots/12-wireshark-ttl-5.png)
```

## Conclusion

Static routes provide direct control over how traffic reaches remote networks. The routing tables and connectivity tests help verify the configuration, while traceroute and Wireshark show how TTL expiration and ICMP Time Exceeded messages reveal the packet's path.
