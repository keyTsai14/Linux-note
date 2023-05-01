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
