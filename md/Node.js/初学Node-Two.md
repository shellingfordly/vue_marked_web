# 连接远程服务器

mac使用自带终端。

window使用Xshell第三方工具，Xshell连接方式看菜鸟教程

mac为例：

```shell
#终端输入以下命令 回车(输入本机密码)
sudo su -

#然后输入 ssh -p 端口号(ssh端口号是22) 服务器用户名(默认root)@服务器公网ip  例如
ssh -p 22 root@47.92.153.88
#然后回车  输入yes确认 回车
#然后输入服务器密码
#然后看到类似：[root@iz8vb34affxrx2bxh3qwz1z ~]#  表示登录成功
```

# 安装nodejs

## 安装

```shell
# 复制回车就行
wget https://nodejs.org/dist/v10.8.0/node-v10.8.0-linux-x64.tar.xz
#回车，等待安装成功   
```

## 解压

```shell
tar xvf node-v10.7.0-linux-x64.tar.xz
```

## 移动

```shell
# mv命令移动并改名
mv node-v10.7.0-linux-x64 /usr/local/node
```

## 配置命令

```shell
vi ~/.bash_profile
# 在 ~/.bash_profile 回车打开的文件里按 i 编辑，然后在文件的export PATH前一行添加
PATH=$PATH:/usr/local/node/bin
# 然后退出保存文件 :wq
# 运行
source ~/.bash_profile

# node -v npm -v 查看node和npm命令是否配置成功
```

到此nodejs安装成功