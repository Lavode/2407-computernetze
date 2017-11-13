# R1

## Assign addresses to interfaces

```
conf t
interface fastEthernet 0/0
ip address 10.0.1.1 255.255.255.0
no shutdown
end

conf t
interface fastEthernet 0/1
ip address 10.0.100.1 255.255.255.0
no shutdown
end
```

## Static routing

```
conf t
ip route 10.0.200.0 255.255.255.0 10.0.100.2
ip route 10.0.2.0 255.255.255.0 10.0.100.2
ip route 10.0.3.0 255.255.255.0 10.0.100.2
end
```

# R2

## Assign addresses to interfaces

```
conf t
interface fastethernet 0/0
ip address 10.0.100.2 255.255.255.0
no shutdown
end

conf t
interface fastethernet 0/1
ip address 10.0.200.1 255.255.255.0
no shutdown
end

conf t
interface fastethernet 1/0
! Configure port in L3 mode
no switchport
ip address 10.0.2.1 255.255.255.0
no shutdown
end
```

## Static routing

```
conf t
ip route 10.0.1.0 255.255.255.0 10.0.100.0
ip route 10.0.3.0 255.255.255.0 10.0.200.2
end
```

# R3

## Assign addresses to interfaces

```
conf t
interface fastethernet 0/1
ip address 10.0.3.1 255.255.255.0
no shutdown
end

conf t
interface fastethernet 0/0
ip address 10.0.200.2 255.255.255.0
no shutdown
end
```

## Static routing

```
conf t
ip route 10.0.1.0 255.255.255.0 10.0.200.1
ip route 10.0.2.0 255.255.255.0 10.0.200.1
ip route 10.0.100.0 255.255.255.0 10.0.200.1
end
```

