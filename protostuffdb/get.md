# get results (all vps run on ubuntu 16.04 x64)

10M iterations

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 188 ms | total: 240 ms
elapsed ms: 57,006 | ops/sec: 175,419 | response body bytes: 80
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 93 ms | total: 173 ms
elapsed ms: 48,141 | ops/sec: 207,723 | response body bytes: 80
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 92 ms | total: 175 ms
elapsed ms: 55,611 | ops/sec: 179,817 | response body bytes: 80
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 110 ms | total: 231 ms
elapsed ms: 242,282 | ops/sec: 41,274 | response body bytes: 80
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 233 ms | total: 408 ms
elapsed ms: 269,543 | ops/sec: 37,099 | response body bytes: 80
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 231 ms | total: 414 ms
elapsed ms: 59,473 | ops/sec: 168,141 | response body bytes: 80
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 228 ms | total: 486 ms
elapsed ms: 69,524 | ops/sec: 143,834 | response body bytes: 80
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 135 ms | total: 252 ms
elapsed ms: 67,610 | ops/sec: 147,906 | response body bytes: 80
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 149 ms | total: 302 ms
elapsed ms: 61,684 | ops/sec: 162,115 | response body bytes: 80
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/get.json
protostuffdb
jni rpc: 79 ms | total: 147 ms
elapsed ms: 42,744 | ops/sec: 233,946 | response body bytes: 80
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 85 ms | total: 157 ms
elapsed ms: 42,482 | ops/sec: 235,389 | response body bytes: 80
```

