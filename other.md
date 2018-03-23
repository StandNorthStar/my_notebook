python:

1. django 例题做出来.

   此第二十三题[https://github.com/Yixiaohan/show-me-the-code](https://github.com/Yixiaohan/show-me-the-code)

   要求: 从数据库读取然后显示到前台.

2. restful api接口如何编写

```
serializers里面的 class Mate\(\): 下 fields 和 excloud 作用
```

1. 重写ansible API, 调用playbook执行脚本.

   如果不太清楚可以画出流程图

   django主要和页面进行交互;

   ```
    页面调用的时候根据url把request的参数传递给对应view.py类. 

    类接收执行
   ```

2. Python基础面试题, 多做多记

---

自动化运维平台ansible, 添加/执行/删除 动作

1. 前端添加ansible模块任务时, 后台执行流程

2. 前端删除ansible模块任务时, 后台执行流程

3. 执行任务

4. ansible执行任务时,用户无感知. 任务在后台执行.

---

python

---

django 的models 和数据库之间怎么交互, 怎么获取到数据传递到view上的.  \(manager\)

---

openstack

---

vm获取dhcp的流程  \[从dnsmasq获取IP地址\]

```
\# vm获取IP前的步骤:

1. 创建的port\(IP地址和MAC\) neutron会把它同步到dnsmasq里面.

2. nova-compute 会设置vm的MAC地址



\# vm获取IP地址:

1. vm开机启动发出dhcpdiscover广播.

2. 广播到达veth tap ,然后传送给veth pair的另一端namespace, dnsmasq检查其host文件, 
   发现有对应项, 于是dnsmasq以DHCPOFFER消息将IP/子网/租期等发送给vm

3. vm发送dhcpquest消息接受此dhcpoffer

4. dnsmasq发送确认消息 dhcpack 



namespace如何隔离dnsmasq
```

vxlan下vm的上网网络流程.

```
  https://www.cnblogs.com/CloudMan6/p/6058985.html
```

vxlan模式下vm之间是怎么通信

linuxbridge和openvswitch有什么区别

cinder模块的作用, 可以接哪些存储.

---

ceph

