# socket

src/net/sock\_posix.go

pakage net

返回 一个socket文件描述符

func socket\(net string, family, sotype, proto int, ipv6only bool, laddr, raddr sockaddr, deadline time.Time, cancel &lt;-chan struct{}\) \(fd \*netFD, err error\) {

	s, err := sysSocket\(family, sotype, proto\)

	if err != nil {

		return nil, err

	}

	if err = setDefaultSockopts\(s, family, sotype, ipv6only\); err != nil {

		closeFunc\(s\)

		return nil, err

	}

	if fd, err = newFD\(s, family, sotype, net\); err != nil {

		closeFunc\(s\)

		return nil, err

	}

