# docker-openvpn

### Configuration

Replace `domainname` and `username`

    docker run -v /opt/openvpn/data:/etc/openvpn --rm kylemanna/openvpn ovpn_genconfig -u udp://{domainname}
    docker run -v /opt/openvpn/data:/etc/openvpn --rm -it kylemanna/openvpn ovpn_initpki

    docker run -v /opt/openvpn/data:/etc/openvpn --rm -it kylemanna/openvpn easyrsa build-client-full {username} nopass
    docker run -v /opt/openvpn/data:/etc/openvpn --rm kylemanna/openvpn ovpn_getclient {username} > {username}.ovpn
    
    docker-compose up -d

### With another interface

    # VPN public
    auto eth0:0
    iface eth0:0 inet static
        address 0.0.0.0
        netmask 255.255.255.255

    auto br0
    iface br0 inet static
        bridge_ports eth0.0
        address 172.18.0.2
        netmask 255.255.255.0
        broadcast 172.18.0.255
        gateway 172.18.0.1
