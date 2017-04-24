# Request

／src/net/request.go

package http

标示服务端收到的或者客户端发出的http请求，客户端和服务端用法基本一样

type Request struct {

Method string //区分请求类型\(GET, POST, PUT, etc.\)

URL \*url.URL//区分URL是被服务端请求的还是客户端发出的请求

对于客户端请求，多数情况下是空的

对于服务端被请求的URL从 RequestURI的Request-Line 提取

Proto      string // "HTTP/1.0"  //http 版本 HTTP/1.1 or HTTP/2

```
ProtoMajor int    // 1

ProtoMinor int    // 0
```

Header Header //请求头，如果服务器收到请求如下：

```
   //    Host: example.com

//    accept-encoding: gzip, deflate

//    Accept-Language: en-us

//    fOO: Bar

//    foo: two

//
```

存储格式如下

```
//

//    Header = map\[string\]\[\]string{

//        "Accept-Encoding": {"gzip, deflate"},

//        "Accept-Language": {"en-us"},

//        "Foo": {"Bar", "two"},

//    }
```

对于客户端请求头存在Request.Host，而不是Header map

http协议定义头部不区分大小写，请求解析器，把它解析成驼峰格式

对于客户端请求，请求头部，比如Content-Length和Connection会被自动填写，Header里面的内容会被忽略

Body io.ReadCloser//请需求内容，当返回EOF符的时候会关闭请求体，但是没必要关闭连接

ContentLength int64 // 内容长度，－1标示未知

TransferEncoding \[\]string //从最外到最内编码方式

Close bool //服务端会自动处理，不关注这个字段，客户端会看 Transport.DisableKeepAlives 是否被设置

Host string //"host:port"

Form url.Values  // 包含URL里面的参数和POST或者PATH  PUT 参数，只有ParseForm 方法被调用后才有用

PostForm url.Values //POST或者PATH  PUT 参数，只有ParseForm 方法被调用后才有用

MultipartForm \*multipart.Form //解析multipart form 包括文件上传

Trailer Header//请求体后加的额外headers，

RemoteAddr string //记录发送请求的ip和端口，一般供日志使用

RequestURI string //未被修改的 Request-URI

TLS \*tls.ConnectionState//记录接受到请求的TLS，

Cancel &lt;-chan struct{}//只有客户端可用，表示连接是因为取消关闭的

｝

