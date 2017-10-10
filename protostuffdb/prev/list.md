# list results (all vps run on ubuntu 16.04 x64)

1M iterations
- 30 entries fetched per iteration (reverse scan, latest first)

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 150 ms | total: 201 ms
elapsed ms: 31,557 | ops/sec: 31,687 | response body bytes: 2,052
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
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 35 ms | total: 117 ms
elapsed ms: 36,906 | ops/sec: 27,095 | response body bytes: 2,052
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 35 ms | total: 117 ms
elapsed ms: 29,232 | ops/sec: 34,209 | response body bytes: 2,052
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
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 71 ms | total: 176 ms
elapsed ms: 77,841 | ops/sec: 12,846 | response body bytes: 2,052
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 156 ms | total: 310 ms
elapsed ms: 41,134 | ops/sec: 24,310 | response body bytes: 2,052
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
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 71 ms | total: 275 ms
elapsed ms: 48,032 | ops/sec: 20,819 | response body bytes: 2,052
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 85 ms | total: 289 ms
elapsed ms: 40,995 | ops/sec: 24,392 | response body bytes: 2,052
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
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 33 ms | total: 140 ms
elapsed ms: 41,833 | ops/sec: 23,904 | response body bytes: 2,052
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 45 ms | total: 158 ms
elapsed ms: 32,098 | ops/sec: 31,153 | response body bytes: 2,052
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
./run-uri.sh protostuffdb /todo/user/Todo/list payload/list.json 1000000
protostuffdb
jni rpc: 35 ms | total: 101 ms
elapsed ms: 29,315 | ops/sec: 34,111 | response body bytes: 2,052
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 34 ms | total: 97 ms
elapsed ms: 25,720 | ops/sec: 38,879 | response body bytes: 2,052
```

