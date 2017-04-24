# Mutex



／src/sync/mutex.go

package  sync

0 标示未加锁

type Mutex struct {

	state int32

	sema  uint32

}

