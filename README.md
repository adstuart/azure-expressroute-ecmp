# ExpressRoute outbound ECMP

- All testing done in West Europe region.
- All outputs show effective-routes from Spoke VM NIC

# Single circuit (Primary/Secondary paths same AS-Path)

![Alt text](/single.png)

## VNG

ECMP outbound over two links as expected.

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.37
```

![Alt text](/equal.png)

## VNG + ARS

ECMP broken outbound, single link used as per open documented bug [here](https://learn.microsoft.com/en-us/azure/route-server/troubleshoot-route-server#why-is-the-equal-cost-multi-path-ecmp-function-of-my-expressroute-turned-off-after-i-deploy-azure-route-server-to-the-virtual-network).

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
```

![Alt text](/unequal.png)

## VWAN + RI

ECMP outbound over two links - official support pending.

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.37
```

## VWAN (New Hub October 2023)

ECMP outbound over two links - official support pending.

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.37
```

# Dual circuits (4 paths, all same AS-Path)

![Alt text](/dual.png)

## VNG

ECMP outbound over four links as expected.

```
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.56
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.57
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.20.88.55
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.20.88.56
```

## VNG + ARS

ECMP broken outbound, single link used as per open documented bug [here](https://learn.microsoft.com/en-us/azure/route-server/troubleshoot-route-server#why-is-the-equal-cost-multi-path-ecmp-function-of-my-expressroute-turned-off-after-i-deploy-azure-route-server-to-the-virtual-network).

```
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.56
```

# Beyond 4 pathes (Beyond 2 circuits)

![Alt text](/dublin.png)

### VNG

ECMP outbound over five links. Up to Azure SDN limit of 8 links.

```
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.56
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.57
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.20.88.110
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.20.88.55
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.20.88.56

```

