* Video : Safari Link, [https://www.safaribooksonline.com/library/view/concurrent-and-parallel/9781771375313/]

# Multi-processing
* Fork vs exec -> fork returns 0 for child process, pid in parent process, -1 for error
* exec will replace the current process while fork will copy the current process into a new one
* ways to do IPC locally -> signals, named/unnamed pipes, local file, sockets/uds, queues, shared memory
* shared memory ->shmget(...) gets memory, shmat(...) attaches memory block to address space of current process
* shm is faster than using local file, because file will be on the disk.
