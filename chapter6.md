# HandleFunc

/src/net/http/server.go

package http

func HandleFunc\(pattern string, handler func\(ResponseWriter, \*Request\)\) {

```
DefaultServeMux.HandleFunc\(pattern, handler\)
```

}

var DefaultServeMux = NewServeMux\(\)

func NewServeMux\(\) \*ServeMux { return &ServeMux{m: make\(map\[string\]muxEntry\)} }

用请求URL匹配注册的正则，然后选取最接近的正则，匹配对应的处理函数，／ 可以匹配所有未匹配的正则

type ServeMux struct {

```
mu    sync.RWMutex

m     map\[string\]muxEntry

hosts bool // whether any patterns contain hostnames
```

}



