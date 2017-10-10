## setup
```sh
mkdir -p tmp/tars/todo-linux-bench-x64

wget 'https://onedrive.live.com/download?cid=73A9A646B31A141F&resid=73A9A646B31A141F%21322&authkey=AMyHMazemCFOuHo' -O tmp/tars/todo-linux-bench-x64.tar.gz

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
