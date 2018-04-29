# docker-openvpn

### Configuration

Replace `domainname` and `username`

    docker run -v /opt/openvpn/data:/etc/openvpn --rm kylemanna/openvpn ovpn_genconfig -u udp://{domainname}
    docker run -v /opt/openvpn/data:/etc/openvpn --rm -it kylemanna/openvpn ovpn_initpki

    docker run -v /opt/openvpn/data:/etc/openvpn --rm -it kylemanna/openvpn easyrsa build-client-full {username} nopass
    docker run -v /opt/openvpn/data:/etc/openvpn --rm kylemanna/openvpn ovpn_getclient {username} > {username}.ovpn
    
    docker-compose up -d
