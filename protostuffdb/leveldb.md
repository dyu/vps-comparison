# leveldb results (all vps run on ubuntu 16.04 x64)

**create** @ 10M iterations (a single iteration inserts 1 primary key and 1 secondary key)
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
```

**get** @ 10M iterations (no disk seeks, same key used per iteration, the sst will be cached by the filesystem)
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
```

**list** @ 1M iterations (30 entries fetched per iteration, reverse scan, latest first)
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)
**create**
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 189 ms | total: 249 ms
elapsed ms: 116,729 | ops/sec: 85,668 | response body bytes: 80

du -sh target/data/main/user
164M	target/data/main/user
```

**get**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 243 ms | total: 295 ms
elapsed ms: 59,722 | ops/sec: 167,441 | response body bytes: 80
```

**list**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 443 ms | total: 495 ms
elapsed ms: 34,108 | ops/sec: 29,318 | response body bytes: 2,052

du -sh target/data/main/user
160M	target/data/main/user
```

## aws ec2 micro - 990M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            488M     0  488M   0% /dev
tmpfs           100M   11M   89M  11% /run
/dev/xvda1      7.7G  2.2G  5.6G  28% /
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           496M     0  496M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/901
```

**create**
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 40 ms | total: 127 ms
elapsed ms: 83,687 | ops/sec: 119,492 | response body bytes: 80

du -sh target/data/main/user
161M	target/data/main/user
```

**get**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 78 ms | total: 158 ms
elapsed ms: 47,144 | ops/sec: 212,111 | response body bytes: 80
```

**list**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 36 ms | total: 114 ms
elapsed ms: 37,101 | ops/sec: 26,952 | response body bytes: 2,052

du -sh target/data/main/user
163M	target/data/main/user
```

## gcloud micro - 585M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            286M     0  286M   0% /dev
tmpfs            59M  6.5M   53M  11% /run
/dev/sda1        30G  2.4G   27G   9% /
tmpfs           294M     0  294M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           294M     0  294M   0% /sys/fs/cgroup
tmpfs            59M     0   59M   0% /run/user/901
```

**create**
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 38 ms | total: 137 ms
elapsed ms: 515,822 | ops/sec: 19,386 | response body bytes: 80

du -sh target/data/main/user
161M	target/data/main/user
```

**get**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 125 ms | total: 237 ms
elapsed ms: 207,442 | ops/sec: 48,206 | response body bytes: 80
```

**list**
```

```

## vultr - 488M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            225M     0  225M   0% /dev
tmpfs            49M  5.6M   44M  12% /run
/dev/vda1        20G  7.9G   11G  43% /
tmpfs           245M     0  245M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           245M     0  245M   0% /sys/fs/cgroup
tmpfs            49M     0   49M   0% /run/user/901
```

**create**
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 63 ms | total: 241 ms
elapsed ms: 117,637 | ops/sec: 85,007 | response body bytes: 80

du -sh target/data/main/user
161M	target/data/main/user
```

**get**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 170 ms | total: 369 ms
elapsed ms: 64,667 | ops/sec: 154,638 | response body bytes: 80
```

**list**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 85 ms | total: 277 ms
elapsed ms: 46,606 | ops/sec: 21,456 | response body bytes: 2,052

du -sh target/data/main/user
164M	target/data/main/user
```

## linode - 989M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        20G  1.3G   18G   7% /
devtmpfs        493M     0  493M   0% /dev
tmpfs           495M     0  495M   0% /dev/shm
tmpfs           495M  7.7M  488M   2% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           495M     0  495M   0% /sys/fs/cgroup
tmpfs            99M     0   99M   0% /run/user/901
```

**create**
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 39 ms | total: 138 ms
elapsed ms: 95,647 | ops/sec: 104,550 | response body bytes: 80

du -sh target/data/main/user
161M	target/data/main/user
```

**get**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 103 ms | total: 203 ms
elapsed ms: 60,288 | ops/sec: 165,869 | response body bytes: 80
```

**list**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 40 ms | total: 139 ms
elapsed ms: 41,332 | ops/sec: 24,194 | response body bytes: 2,052

du -sh target/data/main/user
163M	target/data/main/user
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            477M     0  477M   0% /dev
tmpfs           100M  5.4M   94M   6% /run
/dev/vda1        30G  1.8G   27G   7% /
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           497M     0  497M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/901
```

**create**
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 34 ms | total: 101 ms
elapsed ms: 68,193 | ops/sec: 146,642 | response body bytes: 80

du -sh target/data/main/user
161M	target/data/main/user
```

**get**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 68 ms | total: 140 ms
elapsed ms: 41,920 | ops/sec: 238,544 | response body bytes: 80
```

**list**
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 35 ms | total: 100 ms
elapsed ms: 29,485 | ops/sec: 33,914 | response body bytes: 2,052

du -sh target/data/main/user
163M	target/data/main/user
```

