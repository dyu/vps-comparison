# hyperleveldb results (all vps run on ubuntu 16.04 x64)

**create** @ 10M iterations (a single iteration inserts 1 primary key and 1 secondary key)
```
./run-uri.sh hprotostuffdb /todo/user/Todo/create payload/create.json
```

**get** @ 10M iterations (no disk seeks, same key used per iteration, the sst will be cached by the filesystem)
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
```

**list** @ 1M iterations (30 entries fetched per iteration, reverse scan, latest first)
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)
**create**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/create payload/create.json
hprotostuffdb
jni rpc: 197 ms | total: 249 ms
elapsed ms: 109,841 | ops/sec: 91,040 | response body bytes: 80

du -sh target/data/main/user
165M	target/data/main/user
```

**get**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 285 ms | total: 336 ms
elapsed ms: 56,325 | ops/sec: 177,538 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 156 ms | total: 208 ms
elapsed ms: 28,410 | ops/sec: 35,198 | response body bytes: 2,052

du -sh target/data/main/user
159M	target/data/main/user
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
./run-uri.sh hprotostuffdb /todo/user/Todo/create payload/create.json
hprotostuffdb
jni rpc: 32 ms | total: 116 ms
elapsed ms: 122,352 | ops/sec: 81,731 | response body bytes: 80

du -sh target/data/main/user
174M	target/data/main/user
```

**get**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 130 ms | total: 215 ms
elapsed ms: 54,058 | ops/sec: 184,985 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 33 ms | total: 117 ms
elapsed ms: 33,724 | ops/sec: 29,651 | response body bytes: 2,052

du -sh target/data/main/user
159M	target/data/main/user
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
./run-uri.sh hprotostuffdb /todo/user/Todo/create payload/create.json
hprotostuffdb
jni rpc: 103 ms | total: 329 ms
elapsed ms: 156,486 | ops/sec: 63,903 | response body bytes: 80

du -sh target/data/main/user
167M	target/data/main/user
```

**get**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 290 ms | total: 548 ms
elapsed ms: 60,783 | ops/sec: 164,517 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 60 ms | total: 277 ms
elapsed ms: 36,073 | ops/sec: 27,721 | response body bytes: 2,052

du -sh target/data/main/user
159M	target/data/main/user
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
./run-uri.sh hprotostuffdb /todo/user/Todo/create payload/create.json
hprotostuffdb
jni rpc: 37 ms | total: 145 ms
elapsed ms: 144,036 | ops/sec: 69,427 | response body bytes: 80

du -sh target/data/main/user
166M	target/data/main/user
```

**get**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 180 ms | total: 329 ms
elapsed ms: 61,588 | ops/sec: 162,366 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 40 ms | total: 149 ms
elapsed ms: 31,046 | ops/sec: 32,209 | response body bytes: 2,052

du -sh target/data/main/user
159M	target/data/main/user
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
./run-uri.sh hprotostuffdb /todo/user/Todo/create payload/create.json
hprotostuffdb
jni rpc: 37 ms | total: 102 ms
elapsed ms: 121,494 | ops/sec: 82,308 | response body bytes: 80

du -sh target/data/main/user
171M	target/data/main/user
```

**get**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/get.json
hprotostuffdb
jni rpc: 128 ms | total: 236 ms
elapsed ms: 50,643 | ops/sec: 197,457 | response body bytes: 80
```

**list**
```
./run-uri.sh hprotostuffdb /todo/user/Todo/list payload/list.json 1000000
hprotostuffdb
jni rpc: 42 ms | total: 107 ms
elapsed ms: 26,384 | ops/sec: 37,900 | response body bytes: 2,052

du -sh target/data/main/user
159M	target/data/main/user
```

