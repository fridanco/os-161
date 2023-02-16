# os-161
The purpose of this project is to support running multiple processes at once from actual compiled programs stored on disk. These programs will be loaded into OS161 and executed in user mode, under the control of your kernel and the command shell in bin/sh (menu command: p bin/sh).
If it is possible to have several processes at the same time, it is necessary to synchronize them to protect the shared ones. We have used lock, mutex lock and cv to protect the critical sections created.
The files modified and added for the shell to work are:
1. arch/mips/syscall/syscall.c;
2.  arch/mips/locore/trap.c;
3.  main/menu.c;
4.  proc/proc.c;
5.  syscall/file_syscalls;
6.  syscall/proc_syscalls;
and their relative .h files.
## SystemCall
In kern/arch/mips/syscall/syscall.c we have enabled the following syscalls by inserting them in the switch case statement managing the values received from the trapframe and the return values.
Error handling, which must agree with the manual of os161, is done through the use of the err parameter. Should an error occur, the variable err will take on the value described in the manual. In the event of a success, the variable is 0.
A short list of what we have add: execv, fork, getppid, getpid, exit, read, write.