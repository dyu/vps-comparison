# leveldb (with log for replication) results (all vps run on ubuntu 16.04 x64)

**create** @ 5M iterations (a single iteration inserts 1 primary key and 1 secondary key)
```
./run-uri.sh protostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
```

**get** @ 10M iterations (no disk seeks, same key used per iteration, the sst will be cached by the filesystem)
```
./run-uri.sh protostuffdb-rmaster /todo/user/Todo/list payload/get.json
```

**list** @ 1M iterations (30 entries fetched per iteration, reverse scan, latest first)
```
./run-uri.sh protostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)
**create**
```
./run-uri.sh protostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
protostuffdb-rmaster
jni rpc: 179 ms | total: 231 ms
elapsed ms: 102,907 | ops/sec: 48,587 | response body bytes: 80

du -sh target/data/main/user
594M	target/data/main/user

ls -alh target/data/main/user/binlogs/rep.log 
-rw-rw-r-- 1 dyu dyu 445M Oct 12 20:48 target/data/main/user/binlogs/rep.log
```

**get**
```
./run-uri.sh protostuffdb-rmaster /todo/user/Todo/list payload/get.json
protostuffdb-rmaster
jni rpc: 293 ms | total: 344 ms
elapsed ms: 58,736 | ops/sec: 170,251 | response body bytes: 80
```

**list**
```
./run-uri.sh protostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
protostuffdb-rmaster
jni rpc: 145 ms | total: 198 ms
elapsed ms: 33,275 | ops/sec: 30,051 | response body bytes: 2,052

du -sh target/data/main/user
584M	target/data/main/user
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
```

**get**
```
```

**list**
```
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
```

**get**
```
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
```

**get**
```
```

**list**
```
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
```

**get**
```
```

**list**
```
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
```

**get**
```
```

**list**
```
```

