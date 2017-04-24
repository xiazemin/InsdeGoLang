# RWMutex

/src/sync/rwmutex.go

package sync

RWMutex 是读写排他锁，可以被多个对象读，一个对象写

type RWMutex struct {

	w           Mutex  // held if there are pending writers

	writerSem   uint32 // semaphore for writers to wait for completing readers

	readerSem   uint32 // semaphore for readers to wait for completing writers

	readerCount int32  // number of pending readers

	readerWait  int32  // number of departing readers

}

