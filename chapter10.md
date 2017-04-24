# Server

src/net/http/server.go

package http

定义了运行http server 所需要的参数

type Server struct {

```
Addr           string //监听的tcp地址
Handler        Handler //即将被唤醒的处理函数
ReadTimeout    time.Duration
WriteTimeout   time.Duration
MaxHeaderBytes int ／／请求头最大字节数
TLSConfig      *tls.Config ／／ ListenAndServeTLS 使用
       // TLSNextProto optionally specifies a function to take over
	// ownership of the provided TLS connection when an NPN
	// protocol upgrade has occurred.  The map key is the protocol
	// name negotiated. The Handler argument should be used to
	// handle HTTP requests and will initialize the Request's TLS
	// and RemoteAddr if not already set.  The connection is
	// automatically closed when the function returns.
	// If TLSNextProto is nil, HTTP/2 support is enabled automatically.
TLSNextProto map[string]func(*Server, *tls.Conn, Handler) ／／
```

｝

