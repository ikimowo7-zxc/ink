# 使用LVM进行完成

请结合磁盘管理这一天的内容，完成以下需求：

添加一块新的磁盘到现有的系统中，要求最终创建一个新的逻辑卷，大小为10GB，名称为 lv_data ，

并格式化为 ext4 文件系统，挂载到 /mnt/data 目录。请简述步骤和命令。





#### 对虚拟机进行挂载一块20G的磁盘，并开机连接远程工具

nvme0n2     259:3    0   20G  0 disk       #查看添加的磁盘

pvcreate /dev/nvme0n2     #转换为物理卷

vgcreate vg_data /dev/nvme0n2  #创建卷组

lvcreate -L 10G -n lv_data vg_data     #创建逻辑卷

mkfs.xfs /dev/vg_data/lv_dat    #对磁盘格式化

mkdir -p /mnt/data     #创建挂载带的目录

mount /dev/vg_data/lv_data /mnt/data     #挂载磁盘

df -h   #查看挂载等相关信息

