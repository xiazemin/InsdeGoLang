# Go http 实例

package main



import \(

	"io"

	"net/http"

\)



func hello\(rw http.ResponseWriter, req \*http.Request\) {

	io.WriteString\(rw, "hello world"\)

}

func main\(\) {

	http.HandleFunc\("/", hello\)

	http.ListenAndServe\(":8001", nil\)

}

package main



import \(

	"io"

	"net/http"

\)



func hello\(rw http.ResponseWriter, req \*http.Request\) {

	io.WriteString\(rw, "hello world"\)

}

func main\(\) {

	http.HandleFunc\("/", hello\)

	http.ListenAndServe\(":8001", nil\)

}



