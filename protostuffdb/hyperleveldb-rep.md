# hyperleveldb results (all vps run on ubuntu 16.04 x64)

**create** @ 5M iterations (a single iteration inserts 1 primary key and 1 secondary key)
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
```

**get** @ 10M iterations (no disk seeks, same key used per iteration, the sst will be cached by the filesystem)
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/get.json
```

**list** @ 1M iterations (30 entries fetched per iteration, reverse scan, latest first)
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)
**create**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
hprotostuffdb-rmaster
jni rpc: 190 ms | total: 242 ms
elapsed ms: 72,189 | ops/sec: 69,261 | response body bytes: 80

du -sh target/data/main/user
648M	target/data/main/user

ls -alh target/data/main/user/binlogs/rep.log 
-rw-rw-r-- 1 dyu dyu 445M Oct 10 16:28 target/data/main/user/binlogs/rep.log
```

**get**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/get.json
hprotostuffdb-rmaster
jni rpc: 280 ms | total: 332 ms
elapsed ms: 66,929 | ops/sec: 149,411 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb-rmaster
jni rpc: 169 ms | total: 221 ms
elapsed ms: 28,707 | ops/sec: 34,833 | response body bytes: 2,052

du -sh target/data/main/user
583M	target/data/main/user
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
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
hprotostuffdb-rmaster
jni rpc: 50 ms | total: 131 ms
elapsed ms: 85,065 | ops/sec: 58,778 | response body bytes: 80

du -sh target/data/main/user
691M	target/data/main/user

ls -alh target/data/main/user/binlogs/rep.log 
-rw-rw-r-- 1 deploy deploy 445M Oct 10 11:16 target/data/main/user/binlogs/rep.log
```

**get**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/get.json
hprotostuffdb-rmaster
jni rpc: 124 ms | total: 284 ms
elapsed ms: 69,954 | ops/sec: 142,950 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb-rmaster
jni rpc: 48 ms | total: 133 ms
elapsed ms: 29,532 | ops/sec: 33,860 | response body bytes: 2,052

du -sh target/data/main/user
583M	target/data/main/user
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
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
hprotostuffdb-rmaster
jni rpc: 49 ms | total: 165 ms
elapsed ms: 517,198 | ops/sec: 9,667 | response body bytes: 80

du -sh target/data/main/user
611M	target/data/main/user

ls -alh target/data/main/user/binlogs/rep.log 
-rw-rw-r-- 1 deploy deploy 445M Oct 10 11:31 target/data/main/user/binlogs/rep.log
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
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
hprotostuffdb-rmaster
jni rpc: 71 ms | total: 183 ms
elapsed ms: 109,952 | ops/sec: 45,474 | response body bytes: 80

du -sh target/data/main/user
628M	target/data/main/user

ls -alh target/data/main/user/binlogs/rep.log 
-rw-rw-r-- 1 deploy deploy 445M Oct 10 11:17 target/data/main/user/binlogs/rep.log
```

**get**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/get.json
hprotostuffdb-rmaster
jni rpc: 288 ms | total: 552 ms
elapsed ms: 82,410 | ops/sec: 121,343 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb-rmaster
jni rpc: 132 ms | total: 402 ms
elapsed ms: 37,923 | ops/sec: 26,368 | response body bytes: 2,052

du -sh target/data/main/user
583M	target/data/main/user
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
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
hprotostuffdb-rmaster
jni rpc: 44 ms | total: 145 ms
elapsed ms: 100,785 | ops/sec: 49,610 | response body bytes: 80

du -sh target/data/main/user
639M	target/data/main/user

ls -alh target/data/main/user/binlogs/rep.log 
-rw-rw-r-- 1 deploy deploy 445M Oct 10 11:17 target/data/main/user/binlogs/rep.log
```

**get**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/get.json
hprotostuffdb-rmaster
jni rpc: 134 ms | total: 243 ms
elapsed ms: 73,509 | ops/sec: 136,037 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb-rmaster
jni rpc: 58 ms | total: 190 ms
elapsed ms: 32,442 | ops/sec: 30,823 | response body bytes: 2,052

du -sh target/data/main/user
583M	target/data/main/user
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
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/create payload/create.json 5000000
hprotostuffdb-rmaster
jni rpc: 38 ms | total: 107 ms
elapsed ms: 84,948 | ops/sec: 58,859 | response body bytes: 80

du -sh target/data/main/user
596M	target/data/main/user

ls -alh target/data/main/user/binlogs/rep.log 
-rw-rw-r-- 1 deploy deploy 445M Oct 10 11:17 target/data/main/user/binlogs/rep.log
```

**get**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/get.json
hprotostuffdb-rmaster
jni rpc: 109 ms | total: 194 ms
elapsed ms: 57,032 | ops/sec: 175,339 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb-rmaster /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb-rmaster
jni rpc: 52 ms | total: 120 ms
elapsed ms: 24,319 | ops/sec: 41,119 | response body bytes: 2,052

du -sh target/data/main/user
583M	target/data/main/user
```

