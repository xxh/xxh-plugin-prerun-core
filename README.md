This plugin adds `xxh-sudo` command to run `sudo` with current session environment: `PATH`, `XXH_HOME`, Python and XDG.

## Install
From xxh repo:
```
xxh +I xxh-plugin-prerun-sudo
```
From any repo:
```
xxh +I xxh-plugin-prerun-sudo+git+https://github.com/xxh/xxh-plugin-prerun-sudo
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
### Usage xxh sudo with xxh python to run http server with API
```bash
xxh +RI xxh-plugin-prerun-sudo xxh-plugin-prerun-python
xxh myhost +s zsh +if

myhost> pip install fastapi uvicorn && mkdir api && cd api
myhost> echo -e 'from fastapi import FastAPI; app = FastAPI()\n@app.get("/")\ndef read_root():\n return {"xxh": "https://github.com/xxh/xxh"}' > main.py 
myhost> xxh-sudo uvicorn main:app --reload --host 0.0.0.0 --port 80                                                     
INFO: Uvicorn running on http://0.0.0.0:80 (Press CTRL+C to quit)
```
```
$ curl http://myhost/                                                                                       
{"xxh":"https://github.com/xxh/xxh"}
```
