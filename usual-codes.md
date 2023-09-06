### code-note

#### how to ssh / easy to ssh
- 1 open the file `config`
  ```bash
  vim ~/.ssh/config
- 2 input next code to edit
  ```bash
  Host a100 # ssh hostname (custom)
    HostName 10.x.x.x   # IP adress
    User username       # username
    Port 22	# port

#### vim info
- when see "no write since last change (add to override)", next command will be helpful:
  ```bash
  # save and close
  :wq
  # close without saving
  :q!

#### history command
  ```bash
  history

  history | grep  [検索したいコマンド]

  # cdコマンドが履歴にあるか調べる場合
  history | grep  cd

  # 履歴を削除する
  history -c

  # del history command
  history -d 番号

  # 履歴をファイルに保存 save history as file
  history -w history.txt

  # 末尾からの10行分表示 see info below last 10
  history 10

  # 一般ユーザー[user]の場合
  cat /home/user/.bash_history

  # rootユーザーの場合
  cat /root/.bash_history

  # コマンド実行の履歴確認
  less ~/.bash_history
  ```

#### how to upload file to cloud

```bash
# local -> 踏み台
scp /path/to/local/file username@remote:/path/to/remote/directory/
```

#### create file
`touch`
```bash
touch filename
```

#### copy file
`cp`
```bash
# copy file with date
cp -p a.txt b/a.txt_`date "+%Y%m%d"`
```

#### move file
`mv`
```bash
# change filename
mv originname targetname

# move file to path
mv originpath targetpath
```

#### create dictionary
`mkdir`
```bash
# new a dictionary
mkdir foldername

# make a dictionary like test/test1/test2/test3
mkdir -p test/test1/test2/test3
```

#### del dictionary
`rmkdir`
```bash
# del dictionary
rmkdir foldername

# make a dictionary like test/test1/test2/test3
rmdir test/test1/test2/test3
```

#### del file or folder
`rm`
```bash
# Force delete
rm -rf [#folder/#file]

# del after confirm 
rm -ri [#folder/#file]
```

#### how to select global ip address
`ifconfig`
```bash

```

`ip addr show`
```bash
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 52:54:00:6e:b2:21 brd ff:ff:ff:ff:ff:ff
    inet 10.0.12.9/22 brd 10.0.15.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::5054:ff:fe6e:b221/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 02:42:2c:bd:67:fc brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever

note:
根据您提供的输出，您的Linux系统有三个网络接口（lo、eth0和docker0），每个接口都有不同的IP地址。以下是每个接口的IP地址信息：

lo（回环接口）:

IPv4 地址: 127.0.0.1
IPv6 地址: ::1
这是回环接口，用于本地通信，通常用于连接到本地主机。

eth0（以太网接口）:

IPv4 地址: 10.0.12.9
IPv6 地址: fe80::5054:ff:fe6e:b221
这是您的以太网接口，它具有全局IP地址（IPv4地址为10.0.12.9），您可以使用它来连接到网络。

docker0（Docker桥接接口）:

IPv4 地址: 172.17.0.1
这是Docker桥接接口的IPv4地址，用于与Docker容器通信。

根据上述信息，您的全局IPv4地址是eth0接口上的10.0.12.9。这是您在网络上识别和连接到您的Linux系统所使用的IP地址。请注意，这个地址是您当前连接到的网络中的局域网IP地址，如果您希望知道您的公共IP地址（全球IP地址），您需要使用外部服务来查询，如之前提到的在线IP查询服务。
```

`ip addr show`
```bash
10.0.12.9 172.17.0.1
```
