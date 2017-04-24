# HandleFunc

/src/net/http/server.go

package http



func HandleFunc\(pattern string, handler func\(ResponseWriter, \*Request\)\) {

	DefaultServeMux.HandleFunc\(pattern, handler\)

}

var DefaultServeMux = NewServeMux\(\)



