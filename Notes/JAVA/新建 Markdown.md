转发

hub集线器

CSMA载波监听



交换机：记录mac地址和端口的映射关系

多个地址可以对应一个端口





路由器

IP 

ARP

根据IP地址查找Mac地址







- Linux

  - 修改主机名：hostnamectl set-hostname name

  - 创建文件：touch xx

  - 编辑文件：vi xx

  - 修改文件为可执行文件：chmod +x filename

  - 运行python脚本：python xx.py

- Mininet

  - 基本操作

    - 启动:mn

    - 查看版本:mn --version

    - 可视化界面 :mininet/mininet/example/miniedit.py

    - ping 所有主机：pingall

  - 创建拓扑

    - 最小拓扑，一个交换机下两台主机：mn --topo minimal

    - 每个交换机连接一个主机，交换机之间相连接(4个主机，4台交换机)：mn --topo linear,4

    - 所有主机都连接到同一个交换机上(3个主机，1台交换机)：mn --topo single,4

    - 定义深度和扇出形成基于树的拓扑（深度，扇出均为2）：mn --topo tree, fanout=2, depth=2

- OpenvSwith

  - 基本操作
    - 启动：ovs-ctl start

  - ovs-vsctl命令使用

    - 网桥:交换机

      - 查看网桥：ovs-vsctl show

      - 创建网桥：ovs-vsctl add-br br-name

      - 删除网桥(如果网桥内有端口，会一并删除)：ovs-vsctl del br-name

    - 端口：交换机的网口。网桥创建后会有一个和网桥同名的端口。

      - 添加端口(端口需要是计算机上的真实网卡)：ovs-vsctl add-port br-name port-name

      - 删除端口：ovs-vsctl del-port br-name port-name

    - 网桥连接控制器（OVS作为SDN交换机连接到SDN控制器）
      - 连接命令：ovs-vsctl set-controller br-name tcp:127.0.0.1:6633

  - ovs-ofctl命令使用

    - 下发流表：ovs-ofctl add-flow

      - 查看下发的流表：ovs-ofctl dump-flows br-name

      - 第一层：入端口，匹配到之后的actions是output:2, 意思是从2端口转发出去。ovs-ofctl add-flow br-name in_port=1,actions=output:2

      - 第二层：匹配Mac地址：dl_src源mac，dl_dst目的mac。匹配到之后的actions是output:2, 意思是从2端口转发出去。ovs-ofctl add-flow br-name dl_src=xx:xx:xx:xx:xx,actions=output:2

      - 