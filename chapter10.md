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

```

｝

