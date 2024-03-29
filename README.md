The core plugin contains:
* `xxh-sudo` command to run `sudo` with current session environment: `PATH`, `XXH_HOME`, Python and XDG.
* `xxh-screen` command to run `screen` command with xxh session. 
* `xxh-tmux`

## Install
From xxh repo:
```
xxh +I xxh-plugin-prerun-core
```
From any repo:
```
xxh +I xxh-plugin-prerun-core+git+https://github.com/xxh/xxh-plugin-prerun-core
```    
Connect:
```
xxh myhost +if
```
Usage:
```
myhost> xxh-sudo bash -c 'echo $PYTHONPATH && whoami'
/home/user/.xxh/.pip
root
```

## Examples 
### Usage xxh-sudo and xxh-screen with xxh python to run http server with API in the background
```bash
xxh +RI xxh-plugin-prerun-core xxh-plugin-prerun-python
xxh myhost +s zsh +if

myhost> pip install fastapi uvicorn && mkdir api && cd api
myhost> echo -e 'from fastapi import FastAPI; app = FastAPI()\n@app.get("/")\ndef read_root():\n return {"xxh": "https://github.com/xxh/xxh"}' > main.py 
myhost> xxh-screen
myhost> xxh-sudo uvicorn main:app --reload --host 0.0.0.0 --port 80                                                     
INFO: Uvicorn running on http://0.0.0.0:80 (Press CTRL+C to quit)

# Press "Ctrl+a d" to detach screen session
```
```
$ curl http://myhost/                                                                                       
{"xxh":"https://github.com/xxh/xxh"}
```
