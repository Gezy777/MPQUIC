### Quic运行

1. 启动Quic服务端
```bash
cd ./example
go build -o server main.go # 编译main.go，输出server
./server -h # 查看命令的参数含义
./server -v # 启动服务端，-v启动详细日志
```

2. 启动Quic客户端
```bash
cd ./example/client
go build -o client main.go # 编译main.go，输出client
./client -h # 查看命令的参数含义
./client -v -m https://server_ip:6121/demo/tiles # 启动客户端，server_ip是服务端的ip，-v启动详细日志，-m启动多路径
```
### 结合mininet仿真
1. 使用mininet运行一个多路径Topo
```bash
cd mininet
sudo python3 fourNodesTopo.py
```
2. 在节点上分别运行客户端和服务端代码进行测试
```bash
# 在h3运行服务端
h3 /home/zxk/App/project/MPQUIC/mpquicByQuicGo/example/server -v > server.log 2>&1 &
# 在h1运行客户端
h1 /home/zxk/App/project/MPQUIC/mpquicByQuicGo/example/client/client -v -m https://10.0.2.2:6121/demo/tiles > client.log 2>&1
```
