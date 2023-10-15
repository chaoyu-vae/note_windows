#### clone()函数：

```c
/*
child_func:即将要创建的线程或者进程的函数
child_stack:是线程使用的堆栈
*/
    
int clone(int (*child_func)(void), void *child_stack, int flags, void *arg)
```



- ##### 用来创建进程、线程的函数，fork()函数等价于clone(2)

- 