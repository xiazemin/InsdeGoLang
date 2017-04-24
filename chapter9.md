# ListenAndServe

/src/net/http/server.go

packag http

监听tcp端口，调用对应的处理函数来处理进来的请求

func ListenAndServe\(addr string, handler Handler\) error {

```
server := &Server{Addr: addr, Handler: handler}

return server.ListenAndServe\(\)
```

}

