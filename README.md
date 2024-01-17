# Aurora Panel

## What is this?

This is a multi-server port rental management panel. You can add multiple servers and ports, and assign them to any registered user. Tenants can conveniently use the assigned ports to perform various operations. Currently, the supported port functionalities are (all functionalities below support running on AMD64 or ARM64 architectures):

- [iptables](https://www.netfilter.org/)
- [socat](http://www.dest-unreach.org/socat/)
- [gost](https://github.com/ginuerzh/gost)
- [ehco](https://github.com/Ehco1996/ehco)
- [realm](https://github.com/zephyrchien/realm)
- [v2ray](https://github.com/v2fly/v2ray-core)
- [brook](https://github.com/txthinking/brook)
- [iperf](https://iperf.fr)
- [haproxy](http://www.haproxy.org)
- [wstunnel](https://github.com/erebe/wstunnel)
- [shadowsocks](https://github.com/shadowsocks)
- [tinyPortMapper](https://github.com/wangyu-/tinyPortMapper)
- [Prometheus Node Exporter](https://github.com/leishi1313/node_exporter)

Currently, all port forwarding functions support `IPV6`. For forwarding methods other than `iptables`, if the transit machine itself has both `IPV4` and `IPV6` network access capabilities, you can use port forwarding to achieve `IPV4 to IPV6` or `IPV6 to IPV4`.

