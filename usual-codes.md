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

#### copy file
```bash
# copy file with date
cp -p a.txt b/a.txt_`date "+%Y%m%d"`
```
