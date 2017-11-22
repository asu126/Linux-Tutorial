### 简单配置
```
sudo tc qdisc ls dev p2p1  //查看规则
sudo tc qdisc del dev eth0 root //删除规则
sudo tc qdisc add dev eth0 root handle 1:0 htb default 10  //添加队列规则
sudo tc class add dev eth0 parent 1:0 classid 1:10 htb rate 70Mbps ceil 75Mbps prio 0 // 添加class规则
sudo tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 10 fw flowid 1:10 //添加filter
sudo iptables -A OUTPUT -t mangle -p tcp --sport 80 -j MARK --set-mark 10 //设置iptable规则
```

### 限制ip段通道流量
在上述队列规则下，添加新的class，filter规则

```
sudo tc class add dev eth0 parent 1:0 classid 1:11 htb rate 20Mbps ceil 20Mbps prio 0 // 添加class规则
sudo tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 11 fw flowid 1:11 //添加filter
# 将所有限制的ip添加到11这个通道中
sudo iptables -t mangle -A POSTROUTING -d 10.184.203.85 -j MARK --set-mark 11
```

###### 参考：https://segmentfault.com/a/1190000000666869
