## Comman commands to be used in the workshop

### Login to workshop image (username/password: appworks/appworks)

```shell
ssh appworks@192.168.99.100
```

### Setup host-only adapter to access guest from host (windows/mac)
- With VM shutdown, choose VM, then Settings/Network. Add an Adapter 2 attached to Host-only Adapter (probably vboxnet0)
Go to VirtualBox top level menu, then Preferences/Network/Host-only Networks
- Click DHCP Server, make sure it's on (this will assign host-only IP to eth1)
- Note the Lower Address Bound. Unless you're running multiple VMs simultaneously using Host-only, this will be your IP

If the Lower Address Bound IP is not 192.168.99.100, follow the below steps
- Boot VM
- Change eth1 settings in `/etc/network/interfaces` file to permit Mac to Guest ssh access:

```shell
vi  /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        hostname appworks

auto eth1
    iface eth1 inet static
        address 192.168.99.100 --> Change this to the IP given in the Lower Address Bound
        netmask 255.255.255.0
```
### Start eclipse che
```shell
docker run \
  -it \
  --rm \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /home/appworks/che-data:/data \
  eclipse/che start
```
