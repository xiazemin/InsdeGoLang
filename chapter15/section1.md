# socket

src/net/ipsock\_posix.go

package net

// Internet sockets \(TCP, UDP, IP\)

func internetSocket\(net string, laddr, raddr sockaddr, deadline time.Time, sotype, proto int, mode string, cancel &lt;-chan struct{}\) \(fd \*netFD, err error\) {

	family, ipv6only := favoriteAddrFamily\(net, laddr, raddr, mode\)

	return socket\(net, family, sotype, proto, ipv6only, laddr, raddr, deadline, cancel\)

}

/net/sock\_posix.go

pakage net

返回 一个socket文件描述符

func socket\(net string, family, sotype, proto int, ipv6only bool, laddr, raddr sockaddr, deadline time.Time, cancel &lt;-chan struct{}\) \(fd \*netFD, err error\) {

```
s, err := sysSocket\(family, sotype, proto\)

if err != nil {

    return nil, err

}

if err = setDefaultSockopts\(s, family, sotype, ipv6only\); err != nil {

    closeFunc\(s\)

    return nil, err

}

if fd, err = newFD\(s, family, sotype, net\); err != nil {

    closeFunc\(s\)

    return nil, err

}
```



