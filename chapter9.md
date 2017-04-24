# ListenAndServe

/src/net/http/server.go

packag http

func ListenAndServe\(addr string, handler Handler\) error {

	server := &Server{Addr: addr, Handler: handler}

	return server.ListenAndServe\(\)

}

