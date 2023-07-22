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
