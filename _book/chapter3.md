# ResponseWrite

/src/net/http/server.go

package http

供http句柄使用的返回结构体

type ResponseWriter interface｛

Header （）Header//http 头部被改写后，这个接口返回http头映射，通过WriteHeader. 来更改http头

Write\(\[\]byte\) \(int, error\) //写http返回，如果没有写头，会调用WriteHeader. ，如果没有指定Content-Type，会尝试通过类容的前512字节反解

WriteHeader\(int\) //返回http响应头和状态，如果没有显示调用，先调用Write方法会触发一个隐式调用 WriteHeader\(http.StatusOK\).

｝

