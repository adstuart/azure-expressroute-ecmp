# ExpressRoute outbound ECMP

All testing done in West Europe region.

# Single circuit (Primary/Secondary routes same AS-Path)

## VNG

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.37
```

## VNG + ARS

```
Virtual network gateway, Active, 192.168.2.0/24, Virtual network gateway, 10.3.129.36
```

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
