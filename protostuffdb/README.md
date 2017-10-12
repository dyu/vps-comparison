## setup
```sh
mkdir -p tmp/tars/todo-linux-bench-x64

# if the machine's jvm resides in /usr/lib/jvm/java-7-oracle 
wget 'https://onedrive.live.com/download?cid=73A9A646B31A141F&resid=73A9A646B31A141F%21326&authkey=ANMSnjyIKXHdaf4' -O tmp/tars/todo-linux-bench-x64.tar.gz
# else
wget 'https://onedrive.live.com/download?cid=73A9A646B31A141F&resid=73A9A646B31A141F%21327&authkey=ADnsfTGjehRsr7I' -O tmp/tars/todo-linux-bench-x64.tar.gz

cd tmp/tars/todo-linux-bench-x64
tar -xzf ../todo-linux-bench-x64.tar.gz
```

## test echo via curl
```sh
cd bench
./run.sh

# on another terminal
curl http://127.0.0.1:5000/todo/user/echoInt -X POST -d @payload/echoInt.json
```

## test bench echo
```sh
# 1M iterations, 1K warmups
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json 1000000 1000
```
