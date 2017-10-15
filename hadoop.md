

# hapdoop
## 安装
http://www.powerxing.com/install-hadoop/
http://blog.csdn.net/hitwengqi/article/details/8008203
http://www.linuxidc.com/Linux/2016-12/138567.htm
http://blog.csdn.net/mark_lq/article/details/53384358

- 1.安装Java

- 2.设置Hadoop用户和组
```
~$ sudo addgroup hadoop
~$ sudo adduser --ingroup hadoop hadoop
# 添加到管理员组
~$ sudo usermod -aG admin hadoop
```

- 3.安装ssh
```
sudo apt-get install openssh-server
ssh-keygen -t rsa -P ""
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
ssh localhost 
```

- 4.安装hadoop
  - 下载https://mirrors.cnnic.cn/apache/hadoop/common/
  - 解压
  - 移动到/usr/local
  - 配置hadoop-env.sh, core-site.xml, hdfs-site.xml, mapred-site.xml，/etc/profile文件
  - 格式化 hadoop namenode –format
  - 启动 sbin/start-all.sh
  - 停止 sbin/stop-all.sh
  - 我们也可以通过网页来看是否正常安装与配置，地址如下：http://localhost:50070/
  
- 5.使用
- hadoop fs -mkdir -p /user/input
- hadoop fs -ls /

wordcount/sort
参考：http://www.imooc.com/video/8069
