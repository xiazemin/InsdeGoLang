# ListenAndServe

／src/net/http/server.go

package http

监听tcp连接，处理对应请求

func \(srv \*Server\) ListenAndServe\(\) error {

	addr := srv.Addr

	if addr == "" {

		addr = ":http"

	}

	ln, err := net.Listen\("tcp", addr\)

	if err != nil {

		return err

	}

	return srv.Serve\(tcpKeepAliveListener{ln.\(\*net.TCPListener\)}\)

}

