## LVM 分区创建

##### 查询当前可挂载物理磁盘
```bash
sudo fdisk -l
```

##### 磁盘分区
```bash
sudo fdisk /dev/vdb
#分别输入 n p 1 回车 回车 t L 8e wq 保存退出
sudo fdisk /dev/vdc
#分别输入 n p 1 回车 回车 t L 8e wq 保存退出
sudo fdisk /dev/vdd
#分别输入 n p 1 回车 回车 t L 8e wq 保存退出
sudo fdisk /dev/vde
#分别输入 n p 1 回车 回车 t L 8e wq 保存退出
```


##### 创建 PV
```bash
sudo pvcreate /dev/vdb1
sudo pvcreate /dev/vdc1
sudo pvcreate /dev/vdd1
sudo pvcreate /dev/vde1
```


##### 创建VG
```bash
sudo vgcreate vg_group /dev/vdb1 /dev/vdc1 /dev/vdd1 /dev/vde1
```


##### 创建LV
```bash
sudo lvcreate -l 100%VG  -n vg_1  vg_group
```

##### 查看 LV path
```bash
sudo lvdisplay
```

##### 格式化 LV  path
```bash
sudo mkfs.ext4 /dev/vg_group/vg_1
```

##### 挂载磁盘
```bash
sudo mount /dev/vg_group/vg_1 /lvm_data
```

##### 设置自动挂载
```bash
sudo vim /etc/fstab
#添加内容
/dev/vg_group/vg_1  /lvm_data   ext4    defaults    0   0
#重新加载挂载
sudo mount -a
```

------------------------------------------------
## LVM 分区扩容

//添加新物理磁盘
//查询当前可挂载物理磁盘
fdisk -l

//磁盘分区
fdisk /dev/vdf
#分别输入 n p 1 回车 回车 t L 8e wq 保存退出

//创建PV
pvcreate /dev/vdf1

//将新的物理卷添加/拉伸到物理卷组中
vgextend vg_group /dev/vdf1

//查看拉伸后的物理卷组大小
vgs

//拉伸逻辑卷
lvextend -l 100%VG /dev/vg_group/vg_1

//拉伸文件系统大小
resize2fs  /dev/vg_group/vg_1
