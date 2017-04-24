# URL

src/net/url/url.go

package url

标示一个已经解析的URL

通用的表达格式是：    scheme://\[userinfo@\]host/path\[?query\]\[\#fragment\]

path 是解码后的格式，/%47%6f%2f 标示成／go／

type URL struct {

```
Scheme   string

Opaque   string    // encoded opaque data

User     \*Userinfo // username and password information

Host     string    // host or host:port

Path     string

RawPath  string // encoded path hint \(Go 1.5 and later only; see EscapedPath method\)//加密后的url

RawQuery string // encoded query values, without '?'

Fragment string // fragment for references, without '\#'
```

}

