# TCPListener

src/net/fd\_unix.go

package  net

tcp连接监听器，客户端应该使用连接器而不是直接使用tcp

type TCPListener struct {

```
fd \*netFD
```

}

// Network file descriptor.

type netFD struct {

	// locking/lifetime of sysfd + serialize access to Read and Write methods

	fdmu fdMutex



	// immutable until Close

	sysfd       int

	family      int

	sotype      int

	isConnected bool

	net         string

	laddr       Addr

	raddr       Addr



	// wait server

	pd pollDesc

}

