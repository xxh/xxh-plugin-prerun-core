This plugin adds `xxh-sudo` command to run `sudo` with current session environment: `PATH`, `XXH_HOME`, `PYTHONPATH`, `PIP_TARGET`.

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
