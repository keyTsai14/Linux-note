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
`ifconfig` or `ip addr show`
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

`hostname -I`
```bash
10.0.12.9 172.17.0.1
```


#### how to know linux architectures(Intel or ARM)
`uname -m`
```bash
如果输出是 "x86_64" 或 "amd64"，则表示你的系统是基于Intel 64位架构的。
如果输出是 "arm" 或 "aarch64"，则表示你的系统是基于ARM架构的。例如，输出为 "armv7l" 表示ARMv7架构。
```

`lscpu`
```bash
在输出中，查找 "Architecture" 行，它会告诉你系统的架构。
如果是 "x86_64"，则为Intel 64位架构，如果是 "aarch64"，则为ARM 64位架构，如果是 "armv7l"，则为ARMv7架构。
```

`cat /proc/cpuinfo`
```bash
在输出中，查找 "CPU architecture" 或 "model name" 行，它们通常会提供有关CPU架构的信息。
同样，"x86_64"表示Intel 64位架构，"aarch64"表示ARM 64位架构，"armv7l"表示ARMv7架构。
```

#### logファイルを出力
```bash
cat */*/*/* | grep t.png | grep "t=c" | grep "c=3" | sort > t-png_itoyokado-20230901_20231018.log

这个命令似乎是在使用一系列的Unix/Linux命令来搜索特定文件并筛选它们的内容，然后将结果保存到一个名为 t-png_itoyokado-20230901_20231018.log 的文件中。让我一步步为您解释这个命令：

cat */*/*/*：这部分命令使用 cat 命令来连接匹配指定模式的文件的内容。模式 */*/*/* 是一个递归模式，匹配位于多个子目录中的文件，例如，它将匹配位于四级子目录中的文件。
|：管道符号（|）用于将上一个命令的输出作为输入传递给下一个命令。
grep t.png：这部分命令使用 grep 命令来搜索输出中包含文本 "t.png" 的行。它筛选包含 "t.png" 的行。
grep "t=c"：这部分命令进一步筛选行，搜索在之前筛选出的行中包含 "t=c" 的内容。
grep "c=3"：这部分命令是另一个筛选器，搜索在之前筛选出的行中包含 "c=3" 的内容。
sort：sort 命令用于按字母顺序对文本行进行排序。
> t-png_itoyokado-20230901_20231018.log：最后，> 符号用于将排序后的输出重定向到一个名为 t-png_itoyokado-20230901_20231018.log 的文件中。

因此，这个命令将处理与特定模式匹配的文件，搜索包含 "t.png"、"t=c" 和 "c=3" 的行，然后对结果进行排序，最后将它们保存到指定的日志文件中。
```

#### grep でAND検索とOR検索をする方法
`grep`
- grepで複数の文字列を検索する方法（OR検索）
書式：`grep -e 【検索文字列】 -e 【検索文字列】 【ファイル名】`
```bash
cat test
Shiga
Kyoto
Osaka
Hyogo
Nara
Wakayama

$ grep -e Kyoto -e Osaka test
Kyoto
Osaka
$ grep -e Kyoto -e Tokyo test
Kyoto
```
`egrep`
- egrepで複数の文字列を検索する方法（OR検索）
書式：`egrep “【検索する文字列】|【検索する文字列】"  【ファイル名】`
```bash
cat test
Shiga
Kyoto
Osaka
Hyogo
Nara
Wakayama

$ egrep "Kyoto|Nara" test
Kyoto
Nara
```
- grepで複数の文字列を絞り込んで検索する方法（AND検索）
書式：`grep 【検索文字列】 【ファイル名】 | grep 【検索文字列】`
