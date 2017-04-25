# ListenTCP

src/net/tcpsock\_posix.go

package  net

监听tcp广播，返回监听器，协议必须是 "tcp", "tcp4", or "tcp6"

如果端口为0，会选择一个可用的端口

func ListenTCP\(net string, laddr \*TCPAddr\) \(\*TCPListener, error\) {

```
switch net {

case "tcp", "tcp4", "tcp6":

default:

    return nil, &OpError{Op: "listen", Net: net, Source: nil, Addr: laddr.opAddr\(\), Err: UnknownNetworkError\(net\)}

}

if laddr == nil {

    laddr = &TCPAddr{}

}

fd, err := internetSocket\(net, laddr, nil, noDeadline, syscall.SOCK\_STREAM, 0, "listen", noCancel\)

if err != nil {

    return nil, &OpError{Op: "listen", Net: net, Source: nil, Addr: laddr, Err: err}

}

return &TCPListener{fd}, nil
```

}

