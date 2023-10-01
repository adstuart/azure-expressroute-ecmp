# ExpressRoute outbound ECMP

- All testing done in West Europe region.
- All outputs show effective-routes from Spoke VM NIC

# Single circuit (Primary/Secondary routes same AS-Path)

![Alt text](/single.png)

## VNG

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.37
```

![Alt text](/equal.png)

## VNG + ARS

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
```

![Alt text](/unequal.png)

## VWAN + RI

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.37
```

## VWAN (New Hub October 2023)

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.37
```

# Dual circuits (4 paths, all same AS-Path)

![Alt text](/dual.png)

## VNG

```
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.56
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.57
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.20.88.55
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.20.88.56
```

## VNG + ARS

```
Virtual network gateway, Active, 172.16.240.0/25, Virtual network gateway, 10.2.146.56
```
