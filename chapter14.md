# Listen

src/net/dial.go

package net

func Listen\(net, laddr string\) \(Listener, error\) {

```
addrs, err := resolveAddrList\("listen", net, laddr, noDeadline\)

if err != nil {

    return nil, &OpError{Op: "listen", Net: net, Source: nil, Addr: nil, Err: err}

}

var l Listener

switch la := addrs.first\(isIPv4\).\(type\) {

case \*TCPAddr:

    l, err = ListenTCP\(net, la\)

case \*UnixAddr:

    l, err = ListenUnix\(net, la\)

default:

    return nil, &OpError{Op: "listen", Net: net, Source: nil, Addr: la, Err: &AddrError{Err: "unexpected address type", Addr: laddr}}

}

if err != nil {

    return nil, err // l is non-nil interface containing nil pointer

}

return l, nil
```

}



