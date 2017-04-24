# HandleFunc

/src/net/http/server.go

package http

注册正则和处理函数

func \(mux \*ServeMux\) HandleFunc\(pattern string, handler func\(ResponseWriter, \*Request\)\) {

```
mux.Handle\(pattern, HandlerFunc\(handler\)\)
```

}

处理正则对应的函数，如果处理已经存在，退出

func \(mux \*ServeMux\) Handle\(pattern string, handler Handler\) {

	mux.mu.Lock\(\)

	defer mux.mu.Unlock\(\)

