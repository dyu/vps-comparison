# insert results (all vps run on ubuntu 16.04 x64)

10M iterations
- a single iteration inserts 1 primary key and 1 secondary key

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
```

*hyperleveldb*
```
./run-uri.sh hprotostuffdb /todo/user/Todo/create payload/create.json
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 196 ms | total: 248 ms
elapsed ms: 114,038 | ops/sec: 87,689 | response body bytes: 80
```

*files*
```
ls -alh target/data/main/user
total 165M
drwxrwxr-x 3 dyu dyu  4.0K Oct  9 19:22 .
drwxrwxr-x 5 dyu dyu  4.0K Oct  9 21:16 ..
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:20 000072.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:20 000075.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:20 000142.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:20 000145.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:20 000148.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000216.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000219.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000222.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000306.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000309.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000312.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000315.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000321.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000322.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000323.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000324.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000325.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000326.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000327.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000328.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000329.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000330.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000331.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000389.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000392.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000415.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000420.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000436.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000440.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000443.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000446.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000449.ldb
-rw-rw-r-- 1 dyu dyu   16K Oct  9 19:21 000451.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000508.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000511.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000514.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000547.ldb
-rw-rw-r-- 1 dyu dyu  836K Oct  9 19:21 000553.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000565.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000571.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000574.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000579.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000582.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000585.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000586.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000635.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000638.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:21 000663.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000677.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000689.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000695.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000698.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000701.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000704.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000707.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000765.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000768.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000771.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000804.ldb
-rw-rw-r-- 1 dyu dyu  552K Oct  9 19:22 000812.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000822.ldb
-rw-rw-r-- 1 dyu dyu  2.0M Oct  9 19:22 000825.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000828.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000831.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000836.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000839.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000842.ldb
-rw-rw-r-- 1 dyu dyu  2.0M Oct  9 19:22 000846.ldb
-rw-rw-r-- 1 dyu dyu 1023K Oct  9 19:22 000856.ldb
-rw-rw-r-- 1 dyu dyu 1021K Oct  9 19:22 000867.ldb
-rw-rw-r-- 1 dyu dyu 1021K Oct  9 19:22 000879.ldb
-rw-rw-r-- 1 dyu dyu 1021K Oct  9 19:22 000890.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000902.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000905.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000908.ldb
-rw-rw-r-- 1 dyu dyu  2.0M Oct  9 19:22 000914.ldb
-rw-rw-r-- 1 dyu dyu 1023K Oct  9 19:22 000924.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000932.ldb
-rw-rw-r-- 1 dyu dyu  1.3M Oct  9 19:22 000939.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000947.ldb
-rw-rw-r-- 1 dyu dyu  1.3M Oct  9 19:22 000953.ldb
-rw-rw-r-- 1 dyu dyu  508K Oct  9 19:22 000956.ldb
-rw-rw-r-- 1 dyu dyu  508K Oct  9 19:22 000958.ldb
-rw-rw-r-- 1 dyu dyu  2.0M Oct  9 19:22 000959.ldb
-rw-rw-r-- 1 dyu dyu  508K Oct  9 19:22 000961.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000962.ldb
-rw-rw-r-- 1 dyu dyu  508K Oct  9 19:22 000964.ldb
-rw-rw-r-- 1 dyu dyu  2.1M Oct  9 19:22 000965.ldb
-rw-rw-r-- 1 dyu dyu  2.4M Oct  9 19:22 000966.log
-rw-rw-r-- 1 dyu dyu  508K Oct  9 19:22 000967.ldb
-rw-rw-r-- 1 dyu dyu   11K Oct  9 19:22 000968.ldb
drwxrwxr-x 2 dyu dyu  4.0K Oct  9 19:20 backup-live
-rw-rw-r-- 1 dyu dyu    16 Oct  9 19:20 CURRENT
-rw-r--r-- 1 dyu dyu     0 Oct  9 19:20 LOCK
-rw-rw-r-- 1 dyu dyu  149K Oct  9 19:22 LOG
-rw-rw-r-- 1 dyu dyu   43K Oct  9 19:22 MANIFEST-000002
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
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 31 ms | total: 114 ms
elapsed ms: 109,169 | ops/sec: 91,600 | response body bytes: 80
```

*files*
```
ls -alh target/data/main/user/
total 168M
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 13:09 .
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 12:11 ..
-rw-rw-r-- 1 deploy deploy  127 Oct  9 13:04 000005.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:07 000079.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:07 000080.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:07 000130.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:07 000131.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000159.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000193.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000243.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000263.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000305.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000351.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000376.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000426.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000454.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000509.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000538.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000601.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000636.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000660.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000670.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000674.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000675.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000678.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000681.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000682.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000685.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000688.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000689.ldb
-rw-rw-r-- 1 deploy deploy 506K Oct  9 13:08 000692.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000694.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000697.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000698.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000699.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000700.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000711.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000723.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000734.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000755.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000765.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000784.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000793.ldb
-rw-rw-r-- 1 deploy deploy 1.4M Oct  9 13:08 000802.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:08 000810.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:09 000818.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000819.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000822.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000823.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000826.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000829.ldb
-rw-rw-r-- 1 deploy deploy 254K Oct  9 13:09 000833.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000895.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000896.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000899.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000934.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000977.ldb
-rw-rw-r-- 1 deploy deploy 247K Oct  9 13:09 000981.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000983.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000995.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001012.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001015.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001025.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001047.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001058.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001078.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001088.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001097.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001114.ldb
-rw-rw-r-- 1 deploy deploy 756K Oct  9 13:09 001122.ldb
-rw-rw-r-- 1 deploy deploy 756K Oct  9 13:09 001130.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001131.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001134.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001135.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001138.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001139.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001206.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001207.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001210.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001237.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001238.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001240.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001241.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001243.ldb
-rw-rw-r-- 1 deploy deploy 1.8M Oct  9 13:09 001244.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001245.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001247.ldb
-rw-rw-r-- 1 deploy deploy 1.3M Oct  9 13:09 001248.ldb
-rw-rw-r-- 1 deploy deploy 766K Oct  9 13:09 001249.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001250.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001252.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001253.ldb
-rw-rw-r-- 1 deploy deploy 2.4M Oct  9 13:09 001254.log
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001255.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001256.ldb
-rw-rw-r-- 1 deploy deploy 428K Oct  9 13:09 001257.ldb
drwxrwxr-x 2 deploy deploy 4.0K Oct  9 12:11 backup-live
-rw-rw-r-- 1 deploy deploy   16 Oct  9 13:07 CURRENT
-rw-r--r-- 1 deploy deploy    0 Oct  9 12:11 LOCK
-rw-rw-r-- 1 deploy deploy 199K Oct  9 13:09 LOG
-rw-rw-r-- 1 deploy deploy  309 Oct  9 13:04 LOG.old
-rw-rw-r-- 1 deploy deploy  61K Oct  9 13:09 MANIFEST-000007
```

*hyperleveldb*
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 60 ms | total: 158 ms
elapsed ms: 643,206 | ops/sec: 15,547 | response body bytes: 80
```

*files*
```
ls -alh target/data/main/user
total 161M
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 13:18 .
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 13:04 ..
-rw-rw-r-- 1 deploy deploy  127 Oct  9 13:07 000005.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000075.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000076.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000121.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000124.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000160.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000198.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000228.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000266.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000306.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000329.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000373.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:10 000422.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:10 000471.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:10 000500.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:11 000558.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:11 000587.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000619.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000620.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000623.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000624.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000625.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000628.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000629.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000632.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000633.ldb
-rw-rw-r-- 1 deploy deploy 512K Oct  9 13:12 000636.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000638.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000639.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000642.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000643.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000653.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000665.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000686.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:12 000697.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:13 000716.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:13 000726.ldb
-rw-rw-r-- 1 deploy deploy 2.0M Oct  9 13:13 000735.ldb
-rw-rw-r-- 1 deploy deploy 1.5M Oct  9 13:13 000751.ldb
-rw-rw-r-- 1 deploy deploy 757K Oct  9 13:13 000759.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:13 000760.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:13 000761.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:13 000762.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:13 000765.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:13 000766.ldb
-rw-rw-r-- 1 deploy deploy 278K Oct  9 13:13 000770.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:14 000832.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:14 000833.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:14 000834.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:14 000879.ldb
-rw-rw-r-- 1 deploy deploy  64K Oct  9 13:14 000883.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:15 000908.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:15 000913.ldb
-rw-rw-r-- 1 deploy deploy 208K Oct  9 13:15 000924.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:15 000940.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:15 000952.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:15 000964.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:15 000985.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:15 000996.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001015.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001025.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001034.ldb
-rw-rw-r-- 1 deploy deploy 1.6M Oct  9 13:16 001051.ldb
-rw-rw-r-- 1 deploy deploy 757K Oct  9 13:16 001059.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001060.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001061.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001064.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001065.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001068.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:16 001071.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:17 001132.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:17 001133.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:17 001178.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:17 001181.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:18 001211.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:18 001221.ldb
-rw-rw-r-- 1 deploy deploy 551K Oct  9 13:18 001222.ldb
-rw-rw-r-- 1 deploy deploy 768K Oct  9 13:18 001225.ldb
-rw-rw-r-- 1 deploy deploy 768K Oct  9 13:18 001237.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:18 001238.ldb
-rw-rw-r-- 1 deploy deploy 768K Oct  9 13:18 001249.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:18 001250.ldb
-rw-rw-r-- 1 deploy deploy 768K Oct  9 13:18 001261.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:18 001262.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:18 001263.ldb
-rw-rw-r-- 1 deploy deploy 509K Oct  9 13:18 001265.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:18 001266.ldb
-rw-rw-r-- 1 deploy deploy 1.1M Oct  9 13:18 001267.ldb
-rw-rw-r-- 1 deploy deploy 2.4M Oct  9 13:18 001268.log
-rw-rw-r-- 1 deploy deploy 509K Oct  9 13:18 001269.ldb
drwxrwxr-x 2 deploy deploy 4.0K Oct  9 13:04 backup-live
-rw-rw-r-- 1 deploy deploy   16 Oct  9 13:07 CURRENT
-rw-r--r-- 1 deploy deploy    0 Oct  9 13:04 LOCK
-rw-rw-r-- 1 deploy deploy 203K Oct  9 13:18 LOG
-rw-rw-r-- 1 deploy deploy   57 Oct  9 13:04 LOG.old
-rw-rw-r-- 1 deploy deploy  62K Oct  9 13:18 MANIFEST-000004
```

*hyperleveldb*
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 83 ms | total: 281 ms
elapsed ms: 156,043 | ops/sec: 64,084 | response body bytes: 80
```

*files*
```
ls -alh target/data/main/user 
total 162M
drwxrwxr-x 3 deploy deploy  4.0K Oct  9 13:10 .
drwxrwxr-x 3 deploy deploy  4.0K Oct  9 13:04 ..
-rw-rw-r-- 1 deploy deploy   127 Oct  9 13:07 000005.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000077.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000078.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000126.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000129.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000157.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000191.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000227.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000267.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000287.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000332.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000380.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000407.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000461.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:08 000488.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000546.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000578.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000633.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000642.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000646.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000647.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000650.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000653.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000654.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000657.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000658.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000661.ldb
-rw-rw-r-- 1 deploy deploy  515K Oct  9 13:09 000662.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000666.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000667.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000668.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000669.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000670.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000680.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000703.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000714.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000725.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000744.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000754.ldb
-rw-rw-r-- 1 deploy deploy  1.9M Oct  9 13:09 000763.ldb
-rw-rw-r-- 1 deploy deploy  1.5M Oct  9 13:09 000779.ldb
-rw-rw-r-- 1 deploy deploy  756K Oct  9 13:09 000787.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000788.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000791.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000792.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000795.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000796.ldb
-rw-rw-r-- 1 deploy deploy  274K Oct  9 13:09 000800.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000862.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000865.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000866.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000913.ldb
-rw-rw-r-- 1 deploy deploy  307K Oct  9 13:09 000917.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000957.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000958.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000963.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:09 000977.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 000992.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001003.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001024.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001035.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001055.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001065.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001075.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001092.ldb
-rw-rw-r-- 1 deploy deploy 1007K Oct  9 13:10 001101.ldb
-rw-rw-r-- 1 deploy deploy  758K Oct  9 13:10 001109.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001110.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001111.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001114.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001117.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001118.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001181.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001184.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001185.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001230.ldb
-rw-rw-r-- 1 deploy deploy  1.8M Oct  9 13:10 001233.ldb
-rw-rw-r-- 1 deploy deploy  768K Oct  9 13:10 001234.ldb
-rw-rw-r-- 1 deploy deploy  767K Oct  9 13:10 001246.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001247.ldb
-rw-rw-r-- 1 deploy deploy  508K Oct  9 13:10 001249.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001250.ldb
-rw-rw-r-- 1 deploy deploy  508K Oct  9 13:10 001252.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001253.ldb
-rw-rw-r-- 1 deploy deploy  2.1M Oct  9 13:10 001254.ldb
-rw-rw-r-- 1 deploy deploy  2.4M Oct  9 13:10 001255.log
-rw-rw-r-- 1 deploy deploy  509K Oct  9 13:10 001256.ldb
-rw-rw-r-- 1 deploy deploy  1.5M Oct  9 13:10 001257.ldb
-rw-rw-r-- 1 deploy deploy  415K Oct  9 13:10 001258.ldb
drwxrwxr-x 2 deploy deploy  4.0K Oct  9 13:04 backup-live
-rw-rw-r-- 1 deploy deploy    16 Oct  9 13:07 CURRENT
-rw-r--r-- 1 deploy deploy     0 Oct  9 13:04 LOCK
-rw-rw-r-- 1 deploy deploy  200K Oct  9 13:10 LOG
-rw-rw-r-- 1 deploy deploy    57 Oct  9 13:04 LOG.old
-rw-rw-r-- 1 deploy deploy   61K Oct  9 13:10 MANIFEST-000004
```

*hyperleveldb*
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 44 ms | total: 170 ms
elapsed ms: 110,326 | ops/sec: 90,640 | response body bytes: 80
```

*files*
```
ls -alh target/data/main/user
total 169M
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 13:09 .
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 13:04 ..
-rw-rw-r-- 1 deploy deploy  127 Oct  9 13:07 000005.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000075.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000078.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000123.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000126.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000153.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000198.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000234.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000253.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000293.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000336.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000384.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000412.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000466.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000496.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000553.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000575.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000583.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000587.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000588.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000591.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000592.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000595.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000598.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000599.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000602.ldb
-rw-rw-r-- 1 deploy deploy 511K Oct  9 13:08 000603.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000607.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000610.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000611.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000620.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000632.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000654.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000665.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000675.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000694.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000703.ldb
-rw-rw-r-- 1 deploy deploy 1.4M Oct  9 13:09 000712.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:09 000720.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:09 000728.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000729.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000730.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000733.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000736.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000737.ldb
-rw-rw-r-- 1 deploy deploy 1.3K Oct  9 13:09 000741.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000801.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000804.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000805.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000850.ldb
-rw-rw-r-- 1 deploy deploy  45K Oct  9 13:09 000854.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000879.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000884.ldb
-rw-rw-r-- 1 deploy deploy 458K Oct  9 13:09 000897.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000900.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000922.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000934.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000955.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000966.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000976.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000995.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001004.ldb
-rw-rw-r-- 1 deploy deploy 1.8M Oct  9 13:09 001021.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:09 001029.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001030.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001033.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001034.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001037.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001038.ldb
-rw-rw-r-- 1 deploy deploy 249K Oct  9 13:09 001044.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001104.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001107.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001108.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001155.ldb
-rw-rw-r-- 1 deploy deploy 309K Oct  9 13:09 001159.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001184.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001191.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001201.ldb
-rw-rw-r-- 1 deploy deploy 462K Oct  9 13:09 001202.ldb
-rw-rw-r-- 1 deploy deploy 766K Oct  9 13:09 001203.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001204.ldb
-rw-rw-r-- 1 deploy deploy 767K Oct  9 13:09 001215.ldb
-rw-rw-r-- 1 deploy deploy 766K Oct  9 13:09 001227.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001228.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001230.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001231.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001233.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001234.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001235.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001237.ldb
-rw-rw-r-- 1 deploy deploy 803K Oct  9 13:09 001238.ldb
-rw-rw-r-- 1 deploy deploy 766K Oct  9 13:09 001239.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001240.ldb
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001242.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001243.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001244.ldb
-rw-rw-r-- 1 deploy deploy 2.4M Oct  9 13:09 001245.log
-rw-rw-r-- 1 deploy deploy 508K Oct  9 13:09 001246.ldb
-rw-rw-r-- 1 deploy deploy 935K Oct  9 13:09 001247.ldb
drwxrwxr-x 2 deploy deploy 4.0K Oct  9 13:04 backup-live
-rw-rw-r-- 1 deploy deploy   16 Oct  9 13:07 CURRENT
-rw-r--r-- 1 deploy deploy    0 Oct  9 13:04 LOCK
-rw-rw-r-- 1 deploy deploy 199K Oct  9 13:09 LOG
-rw-rw-r-- 1 deploy deploy   57 Oct  9 13:04 LOG.old
-rw-rw-r-- 1 deploy deploy  60K Oct  9 13:09 MANIFEST-000004
```

*hyperleveldb*
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

*leveldb*
```
./run-uri.sh protostuffdb /todo/user/Todo/create payload/create.json
protostuffdb
jni rpc: 37 ms | total: 106 ms
elapsed ms: 83,934 | ops/sec: 119,140 | response body bytes: 80
```

*files*
```
ls -alh target/data/main/user
total 162M
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 13:09 .
drwxrwxr-x 3 deploy deploy 4.0K Oct  9 13:04 ..
-rw-rw-r-- 1 deploy deploy  127 Oct  9 13:08 000005.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000077.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000078.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000128.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000129.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000159.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000208.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000227.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000267.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000289.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000331.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000378.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000401.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000454.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000485.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000544.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000574.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000608.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000641.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000678.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000681.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000684.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000685.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000688.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000689.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000692.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000695.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000696.ldb
-rw-rw-r-- 1 deploy deploy 511K Oct  9 13:08 000699.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000701.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000702.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000703.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000704.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000705.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000706.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000718.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000730.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000751.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000762.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000772.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000791.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000800.ldb
-rw-rw-r-- 1 deploy deploy 961K Oct  9 13:08 000809.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:08 000817.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:08 000825.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:08 000826.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000827.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000830.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000831.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000834.ldb
-rw-rw-r-- 1 deploy deploy 498K Oct  9 13:09 000838.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000898.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000901.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000904.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000939.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000981.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000986.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 000998.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001003.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001015.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001038.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001049.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001060.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001080.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001090.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001099.ldb
-rw-rw-r-- 1 deploy deploy 1.8M Oct  9 13:09 001116.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:09 001124.ldb
-rw-rw-r-- 1 deploy deploy 755K Oct  9 13:09 001132.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001133.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001136.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001137.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001140.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001141.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001204.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001207.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001210.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001237.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001238.ldb
-rw-rw-r-- 1 deploy deploy 507K Oct  9 13:09 001240.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001241.ldb
-rw-rw-r-- 1 deploy deploy 507K Oct  9 13:09 001243.ldb
-rw-rw-r-- 1 deploy deploy 1.5M Oct  9 13:09 001244.ldb
-rw-rw-r-- 1 deploy deploy 2.1M Oct  9 13:09 001245.ldb
-rw-rw-r-- 1 deploy deploy 2.4M Oct  9 13:09 001246.log
-rw-rw-r-- 1 deploy deploy 507K Oct  9 13:09 001247.ldb
-rw-rw-r-- 1 deploy deploy 1.1M Oct  9 13:09 001248.ldb
-rw-rw-r-- 1 deploy deploy 605K Oct  9 13:09 001249.ldb
-rw-rw-r-- 1 deploy deploy   16 Oct  9 13:08 CURRENT
-rw-r--r-- 1 deploy deploy    0 Oct  9 13:04 LOCK
-rw-rw-r-- 1 deploy deploy 199K Oct  9 13:09 LOG
-rw-rw-r-- 1 deploy deploy   57 Oct  9 13:04 LOG.old
-rw-rw-r-- 1 deploy deploy  61K Oct  9 13:09 MANIFEST-000004
drwxrwxr-x 2 deploy deploy 4.0K Oct  9 13:04 backup-live
```

*hyperleveldb*
```

```

