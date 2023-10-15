### 日志

- ### binlog

- #### undo log: 事务没有提交前，mysql会先将更新的数据记录到undo log中



### 基础知识总结

- #### 脏读：事务A在执行的过程中，事务B读取了A的修改，但是因为某种原因A没有成功执行，回滚了，那么事务B读取的是个错误的数据

- #### 不可重复读：B事务读取了两次数据，但是因为A事务的修改，两次结果不一样，对于B事务而言就是不可重复读

- #### 可重复读：在同一个事务中反复多次读取数据都是一样的

- #### 隔离级别：

  - ##### 未提交读

  - ##### 提交读（解决了脏读）

  - ##### 可重复读(解决了脏读和不可重复读，<span style="color:red">幻读没有解决</span>)

  - ##### 串行化

- 