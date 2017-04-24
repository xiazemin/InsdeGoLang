# ListenAndServe

／src/net/http/server.go

package http

监听tcp连接，处理对应请求

func \(srv \*Server\) ListenAndServe\(\) error {

```
addr := srv.Addr

if addr == "" {

    addr = ":http"

}

ln, err := net.Listen\("tcp", addr\)

if err != nil {

    return err

}

return srv.Serve\(tcpKeepAliveListener{ln.\(\*net.TCPListener\)}\)
```

}

／／监听请求，并为每一个请求创建一个gorouting

func \(srv \*Server\) Serve\(l net.Listener\) error {

	defer l.Close\(\)

	if fn := testHookServerServe; fn != nil {

		fn\(srv, l\)

	}

	var tempDelay time.Duration // how long to sleep on accept failure

	if err := srv.setupHTTP2\(\); err != nil {

		return err

	}

	for {

		rw, e := l.Accept\(\)

		if e != nil {

			if ne, ok := e.\(net.Error\); ok && ne.Temporary\(\) {

				if tempDelay == 0 {

					tempDelay = 5 \* time.Millisecond

				} else {

					tempDelay \*= 2

				}

				if max := 1 \* time.Second; tempDelay &gt; max {

					tempDelay = max

				}

				srv.logf\("http: Accept error: %v; retrying in %v", e, tempDelay\)

				time.Sleep\(tempDelay\)

				continue

			}

			return e

		}

		tempDelay = 0

		c := srv.newConn\(rw\)

		c.setState\(c.rwc, StateNew\) // before Serve can return

		go c.serve\(\)

	}

}

