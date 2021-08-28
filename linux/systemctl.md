### Linux系统服务管理工具smartctl

受管控的服务需要在<span style="color:red">/usr/lib/systemd/system/</span>目录下创建.service文件.设置的服务可以跟随系统启动而启动。

当服务的配置文件有改动时，需要执行<span style="color:red">sudo systemctl daemon-reload</span>

配置文件的构成：

- Unit 描述信息
  - Description= #描述信息
  - After= #在指定程序前执行
  - Before= #在指定程序后执行
- Service 服务信息
  - Type= #启动类型
    - oneshot :这一选项适用于只执行一项任务、随后立即退出的服务。可能需要同时设置 RemainAfterExit=yes 使得 systemd 在服务进程退出之后仍然认为服务处于激活状态
    - notify: 与 Type=simple 相同，但约定服务会在就绪后向 systemd 发送一个信号。这一通知的实现由 libsystemd-daemon.so 提供。
    - dbus: 若以此方式启动，当指定的 BusName 出现在DBus系统总线上时，systemd认为服务就绪
    - idle: systemd会处理所有的任务后方才执行idle类型的单元
    - simple: 默认值；systemd认为该服务将立即启动，服务进程不会被fork，若是该服务要启动其他服务，除非该服务是socket激活型
  - RemainAfterExit=yes   #通知systemctl结束
  - User= #指定进程服务的权限
  - Group= #指定服务所属的用户组
  - Restart= #是否重复启动
    - always systemctl会不断重启该脚本，适合服务是脚本的
    - no 不会重启，适合程序服务
  - ExecStart=  #后面跟程序的绝对路径，如果有启动参数，后面加上，如果程序没有参数不需要添加ExecStop这条语句
  - ExecStop=   #后面跟程序的绝对路径，如果有停止参数，后面加上
  - PIDFile=   #加上程序PID文件绝对路径
- Install