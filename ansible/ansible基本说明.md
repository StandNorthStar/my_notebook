ansible 运行的基本单元: ansible模块, ansible插件

ansible插件:

```
   connection插件: 连接插件, 根据指定的ssh参数连接指定的服务器

   shell插件: 命令插件,根据sh类型来生成用来connection时要执行的命令

   strategy插件: 执行策略插件, 此插件将任务丢到执行器中执行. \(默认是线性插件,任务一个接一个往下执行.\)

   action插件: 动作插件,实质就是任务模块的所有动作. \(如文件上传等\)
```

ansible执行流程:

1. 通过ansible/cli/adhoc.py来运行, 同时会收集参数信息.

   \(1\). 设置play信息, 然后通过TaskQueueManager运行run;

   \(2\). TaskQueueManager需要Inventory\(节点仓库\), variable\_manager\(收集变量\), options\(命令行中的参数\), stdout\_callbak\(回调函数\)

2. 在task\__queue_\_manager.py 中找到run.

   ```
   \(1\). 初始化时会设置队列.

   \(2\). 会根据options, variable\_manager ,password等信息设置成一个PlayContext信息\(代码位置playbooks/playcontenx.py\)

   \(3\).** 设置**插件\(plugins\)信息/ callback\__loader\(回调\) / strategy\_\_loader\(执行策略\), module_\_loader\(任务模块\)\_

   \(4\). 通过strategy\_loader 插件的run, 去按照顺序执行所有的任务.

   \(5\). 在strate\_loader 执行完run后, 会判断action类型. 如果是meta类型会单独执行\(不是具体的ansible模块\). 而其他模块时, 会加载到队列\_queue\_task

   \(6\). 在队列中会调用workerprocess去处理, 在workerprocess实际run之后, 会使用TaskExecutor进行执行

   \(7\). 在TaskExecutor中会设置connection插件, 并且根据task类型 获取action插件\(就是对应的模块\), 如果模块有自定义的执行,则会执行自动以的action, 如没有会使用nolmal或者async

    (8). 在action插件中定义着执行的顺序, 以及具体操作

    (9). 通过connection插件来执行action的各个操作步骤
   ```

```
参考: https://blog.csdn.net/mx472756841/article/details/53886456
```



