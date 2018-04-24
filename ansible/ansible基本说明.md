ansible 运行的基本单元: ansible模块, ansible插件



ansible插件:

       connection插件: 连接插件, 根据指定的ssh参数连接指定的服务器

       shell插件: 命令插件,根据sh类型来生成用来connection时要执行的命令

       strategy插件: 执行策略插件, 此插件将任务丢到执行器中执行. \(默认是线性插件,任务一个接一个往下执行.\)

       action插件: 动作插件,实质就是任务模块的所有动作. \(如文件上传等\)



ansible执行流程:

      1.  通过ansible/cli/adhoc.py来运行, 同时会收集参数信息. 

            \(1\). 设置play信息, 然后通过TaskQueueManager运行run;

            \(2\). TaskQueueManager需要Inventory\(节点仓库\), variable_manager\(收集变量\), options\(命令行中的参数\), stdout_callbak\(回调函数\)

      2. 在task\__queue_\_manager.py 中找到run.

             \(1\). 初始化时会设置队列.

             \(2\). 会根据options, variable\_manager ,password等信息设置成一个PlayContext信息\(代码位置playbooks/playcontenx.py\)

             \(3\).** 设置**插件\(plugins\)信息/ callback\__loader\(回调\) / strategy\__loader\(执行策略\), module_\_loader\(任务模块\)_

             \(4\). 



