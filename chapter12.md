# tcpKeepAliveListener

src/net/http/server.go

package http

设置tcp连接保持时间，保证无效链接被释放

type tcpKeepAliveListener struct {

	\*net.TCPListener

}

