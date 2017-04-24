# HandleFunc

/src/net/http/server.go

package http

 注册正则和处理函数

func \(mux \*ServeMux\) HandleFunc\(pattern string, handler func\(ResponseWriter, \*Request\)\) {

	mux.Handle\(pattern, HandlerFunc\(handler\)\)

}

