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

```
mux.mu.Lock\(\)

defer mux.mu.Unlock\(\)
// Helpful behavior:
	// If pattern is /tree/, insert an implicit permanent redirect for /tree.
	// It can be overridden by an explicit registration.
	n := len(pattern)
	if n > 0 && pattern[n-1] == '/' && !mux.m[pattern[0:n-1]].explicit {
		// If pattern contains a host name, strip it and use remaining
		// path for redirect.
		path := pattern
		if pattern[0] != '/' {
			// In pattern, at least the last character is a '/', so
			// strings.Index can't be -1.
			path = pattern[strings.Index(pattern, "/"):]
		}
		url := &url.URL{Path: path}
		mux.m[pattern[0:n-1]] = muxEntry{h: RedirectHandler(url.String(), StatusMovedPermanently), pattern: pattern}
	}
}

```



