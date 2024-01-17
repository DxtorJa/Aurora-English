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

### Panel server and controlled machine description

**The panel is recommended to be installed on a separate server, and it is recommended to install it in a VPS with a configuration of no less than 512M memory per core**, and can be deployed directly to the local area. **The controlled machine does not need to do any special configuration, just ensure that the panel server can connect to the controlled machine through ssh. **

When the panel server connects to the controlled machine, it will detect whether the controlled machine has installed python (python must be relied upon by the controlled machine). If it is not installed on the controlled machine, it will automatically perform python installation on the controlled machine through apt/yum (preferred) Install python3), if the controlled machine does not come with python and the automatic installation fails, the panel will display that the controlled machine connection failed (shown as the controlled machine connection status continues to circle).

#### Panel (master) support progress:

- operating system
- [x] CentOS 7+
- [x] Debian 8+
- [x] Ubuntu 18+
- [x] Alpine Linux 3.15.0+ (please use one-click script installation)
- Virtual platform
-[x]KVM
-[x]VMware
- [x] OVZ (requires OVZ to support docker)
- CPU architecture
- [x] AMD64
-[x]ARM64
- Network Type
- [x] IPV4
- [X] IPV6

Special note: Since docker does not enable IPV6 by default, if you need to connect to the controlled machine SSH through IPV6 on the panel, please enable the `ipv6` option in the configuration file of the panel machine and use the `ip6tables` command to add IPV6 NAT to the container, ** No changes are required to the IPV6 address in the command**:

```shell
# 1. Docker-compose.yml configures the ipv6 option. The configuration file is in the ~/aurora/ directory by default.
# Find the line enable_ipv6: false, change false to true, and rebuild the container
cd ~/aurora/ && docker-compose up -d
# 2. Just copy and paste the ip6tables command and press Enter (note that restarting the system will cause the ip6tables rules to be reset and need to be re-added manually)
ip6tables -t nat -A POSTROUTING -s fd00:ea23:9c80:4a54:e242:5f97::/96 -j MASQUERADE
```

