# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G

# random reads
fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
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

*writes*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=5721KiB/s][r=0,w=1430 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19824: Fri Oct  6 04:25:11 2017
  write: IOPS=1453, BW=5813KiB/s (5953kB/s)(1703MiB/300002msec)
    slat (nsec): min=232, max=80365, avg=727.26, stdev=281.53
    clat (usec): min=918, max=47237, avg=2749.72, stdev=2916.36
     lat (usec): min=998, max=47238, avg=2750.45, stdev=2916.37
    clat percentiles (usec):
     |  1.00th=[ 1827],  5.00th=[ 1893], 10.00th=[ 1926], 20.00th=[ 1975],
     | 30.00th=[ 2008], 40.00th=[ 2040], 50.00th=[ 2073], 60.00th=[ 2114],
     | 70.00th=[ 2147], 80.00th=[ 2212], 90.00th=[ 2474], 95.00th=[ 5669],
     | 99.00th=[15795], 99.50th=[18482], 99.90th=[26608], 99.95th=[28967],
     | 99.99th=[35914]
   bw (  KiB/s): min= 3944, max= 6922, per=99.99%, avg=5812.58, stdev=378.06, samples=600
   iops        : min=  986, max= 1730, avg=1453.12, stdev=94.50, samples=600
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=29.53%, 4=64.82%, 10=1.08%, 20=4.17%, 50=0.41%
  cpu          : usr=0.71%, sys=0.29%, ctx=872080, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,436015,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=5813KiB/s (5953kB/s), 5813KiB/s-5813KiB/s (5953kB/s-5953kB/s), io=1703MiB (1786MB), run=300002-300002msec

Disk stats (read/write):
  xvda: ios=0/437518, merge=0/20416, ticks=0/307564, in_queue=307564, util=99.26%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 04:25 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=28.3MiB/s,w=0KiB/s][r=7245,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19845: Fri Oct  6 04:33:34 2017
   read: IOPS=7179, BW=28.0MiB/s (29.4MB/s)(4096MiB/146048msec)
    slat (nsec): min=178, max=73888, avg=304.53, stdev=212.25
    clat (usec): min=19, max=21663, avg=555.96, stdev=649.54
     lat (usec): min=19, max=21663, avg=556.26, stdev=649.54
    clat percentiles (usec):
     |  1.00th=[   24],  5.00th=[   25], 10.00th=[   26], 20.00th=[  208],
     | 30.00th=[  255], 40.00th=[  396], 50.00th=[  424], 60.00th=[  494],
     | 70.00th=[  644], 80.00th=[  799], 90.00th=[ 1004], 95.00th=[ 1270],
     | 99.00th=[ 3523], 99.50th=[ 4490], 99.90th=[ 6783], 99.95th=[ 7767],
     | 99.99th=[11338]
   bw (  KiB/s): min=14896, max=40520, per=99.98%, avg=28711.01, stdev=5676.72, samples=292
   iops        : min= 3724, max=10130, avg=7177.72, stdev=1419.18, samples=292
  lat (usec)   : 20=0.01%, 50=18.84%, 100=0.02%, 250=10.51%, 500=30.90%
  lat (usec)   : 750=15.07%, 1000=14.54%
  lat (msec)   : 2=7.47%, 4=1.97%, 10=0.68%, 20=0.02%, 50=0.01%
  cpu          : usr=1.41%, sys=1.41%, ctx=2097215, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=28.0MiB/s (29.4MB/s), 28.0MiB/s-28.0MiB/s (29.4MB/s-29.4MB/s), io=4096MiB (4295MB), run=146048-146048msec

Disk stats (read/write):
  xvda: ios=357248/13, merge=0/3, ticks=144084/0, in_queue=144076, util=98.75%
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

*writes*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=5345KiB/s][r=0,w=1336 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2363: Fri Oct  6 04:25:15 2017
  write: IOPS=1103, BW=4413KiB/s (4519kB/s)(1293MiB/300051msec)
    slat (nsec): min=189, max=1309.9k, avg=1325.07, stdev=3342.31
    clat (usec): min=1223, max=170629, avg=3620.76, stdev=2928.86
     lat (usec): min=1400, max=170630, avg=3622.09, stdev=2929.00
    clat percentiles (msec):
     |  1.00th=[    3],  5.00th=[    3], 10.00th=[    3], 20.00th=[    3],
     | 30.00th=[    3], 40.00th=[    4], 50.00th=[    4], 60.00th=[    4],
     | 70.00th=[    4], 80.00th=[    5], 90.00th=[    5], 95.00th=[    6],
     | 99.00th=[    9], 99.50th=[   10], 99.90th=[   16], 99.95th=[   35],
     | 99.99th=[  150]
   bw (  KiB/s): min= 1768, max= 6264, per=100.00%, avg=4413.73, stdev=709.59, samples=600
   iops        : min=  442, max= 1566, avg=1103.43, stdev=177.40, samples=600
  lat (msec)   : 2=0.01%, 4=79.12%, 10=20.40%, 20=0.42%, 50=0.02%
  lat (msec)   : 100=0.01%, 250=0.03%
  cpu          : usr=1.07%, sys=0.35%, ctx=662156, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,331031,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=4413KiB/s (4519kB/s), 4413KiB/s-4413KiB/s (4519kB/s-4519kB/s), io=1293MiB (1356MB), run=300051-300051msec

Disk stats (read/write):
  sda: ios=0/336082, merge=0/70071, ticks=0/293508, in_queue=293344, util=92.70%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 04:25 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=924KiB/s,w=0KiB/s][r=231,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2403: Fri Oct  6 04:36:14 2017
   read: IOPS=217, BW=870KiB/s (891kB/s)(255MiB/300044msec)
    slat (nsec): min=100, max=680631, avg=1349.00, stdev=3625.02
    clat (usec): min=28, max=167156, avg=18388.11, stdev=17664.95
     lat (usec): min=28, max=167157, avg=18389.46, stdev=17664.97
    clat percentiles (usec):
     |  1.00th=[    32],  5.00th=[    36], 10.00th=[    40], 20.00th=[    58],
     | 30.00th=[  4883], 40.00th=[ 11731], 50.00th=[ 15270], 60.00th=[ 19792],
     | 70.00th=[ 25297], 80.00th=[ 32113], 90.00th=[ 42206], 95.00th=[ 52167],
     | 99.00th=[ 70779], 99.50th=[ 78119], 99.90th=[100140], 99.95th=[110625],
     | 99.99th=[145753]
   bw (  KiB/s): min=  432, max= 1512, per=100.00%, avg=869.91, stdev=159.06, samples=600
   iops        : min=  108, max=  378, avg=217.46, stdev=39.77, samples=600
  lat (usec)   : 50=16.24%, 100=11.08%, 250=0.91%, 500=0.03%, 750=0.17%
  lat (usec)   : 1000=0.26%
  lat (msec)   : 2=0.89%, 4=0.29%, 10=6.00%, 20=24.84%, 50=33.49%
  lat (msec)   : 100=5.71%, 250=0.10%
  cpu          : usr=0.24%, sys=0.07%, ctx=130519, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=65248,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=870KiB/s (891kB/s), 870KiB/s-870KiB/s (891kB/s-891kB/s), io=255MiB (267MB), run=300044-300044msec

Disk stats (read/write):
  sda: ios=17754/78, merge=0/56, ticks=296700/280, in_queue=296960, util=98.97%
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

*writes*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=26.7MiB/s][r=0,w=6847 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=13903: Fri Oct  6 04:22:57 2017
  write: IOPS=7639, BW=29.8MiB/s (31.3MB/s)(4096MiB/137255msec)
    slat (nsec): min=276, max=592827, avg=829.87, stdev=1491.63
    clat (usec): min=250, max=45881, avg=520.37, stdev=430.37
     lat (usec): min=251, max=45881, avg=521.20, stdev=430.41
    clat percentiles (usec):
     |  1.00th=[  318],  5.00th=[  359], 10.00th=[  388], 20.00th=[  420],
     | 30.00th=[  441], 40.00th=[  461], 50.00th=[  486], 60.00th=[  515],
     | 70.00th=[  545], 80.00th=[  594], 90.00th=[  668], 95.00th=[  734],
     | 99.00th=[  971], 99.50th=[ 1188], 99.90th=[ 2540], 99.95th=[ 4228],
     | 99.99th=[20579]
   bw (  KiB/s): min=23126, max=40136, per=99.99%, avg=30556.05, stdev=3041.75, samples=274
   iops        : min= 5781, max=10034, avg=7639.00, stdev=760.44, samples=274
  lat (usec)   : 500=55.18%, 750=40.38%, 1000=3.55%
  lat (msec)   : 2=0.73%, 4=0.10%, 10=0.04%, 20=0.01%, 50=0.01%
  cpu          : usr=4.18%, sys=3.07%, ctx=2097080, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=29.8MiB/s (31.3MB/s), 29.8MiB/s-29.8MiB/s (31.3MB/s-31.3MB/s), io=4096MiB (4295MB), run=137255-137255msec

Disk stats (read/write):
  vda: ios=7/1057267, merge=0/67350, ticks=4/129068, in_queue=128844, util=71.82%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 04:22 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=22.2MiB/s,w=0KiB/s][r=5693,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=13917: Fri Oct  6 04:26:51 2017
   read: IOPS=5682, BW=22.2MiB/s (23.3MB/s)(4096MiB/184511msec)
    slat (nsec): min=185, max=7276.6k, avg=760.67, stdev=7449.99
    clat (usec): min=26, max=19325, avg=700.73, stdev=335.94
     lat (usec): min=26, max=19326, avg=701.49, stdev=336.07
    clat percentiles (usec):
     |  1.00th=[   66],  5.00th=[  269], 10.00th=[  322], 20.00th=[  474],
     | 30.00th=[  537], 40.00th=[  611], 50.00th=[  685], 60.00th=[  750],
     | 70.00th=[  824], 80.00th=[  914], 90.00th=[ 1037], 95.00th=[ 1156],
     | 99.00th=[ 1598], 99.50th=[ 1991], 99.90th=[ 3195], 99.95th=[ 4178],
     | 99.99th=[ 8225]
   bw (  KiB/s): min=18616, max=28024, per=100.00%, avg=22733.61, stdev=1398.96, samples=369
   iops        : min= 4654, max= 7006, avg=5683.39, stdev=349.73, samples=369
  lat (usec)   : 50=0.24%, 100=1.47%, 250=1.69%, 500=21.10%, 750=35.53%
  lat (usec)   : 1000=27.43%
  lat (msec)   : 2=12.04%, 4=0.44%, 10=0.05%, 20=0.01%
  cpu          : usr=3.10%, sys=2.57%, ctx=2097091, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=22.2MiB/s (23.3MB/s), 22.2MiB/s-22.2MiB/s (23.3MB/s-23.3MB/s), io=4096MiB (4295MB), run=184511-184511msec

Disk stats (read/write):
  vda: ios=662011/39, merge=0/13, ticks=154172/0, in_queue=153948, util=83.48%
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

*writes*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=16.5MiB/s][r=0,w=4229 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=5533: Fri Oct  6 04:23:27 2017
  write: IOPS=5616, BW=21.9MiB/s (23.0MB/s)(4096MiB/186689msec)
    slat (nsec): min=348, max=217027, avg=1029.29, stdev=735.40
    clat (usec): min=282, max=389269, avg=708.40, stdev=5971.55
     lat (usec): min=283, max=389270, avg=709.43, stdev=5971.56
    clat percentiles (usec):
     |  1.00th=[   334],  5.00th=[   355], 10.00th=[   367], 20.00th=[   388],
     | 30.00th=[   408], 40.00th=[   429], 50.00th=[   449], 60.00th=[   478],
     | 70.00th=[   510], 80.00th=[   553], 90.00th=[   619], 95.00th=[   693],
     | 99.00th=[  1020], 99.50th=[  1762], 99.90th=[130548], 99.95th=[158335],
     | 99.99th=[210764]
   bw (  KiB/s): min= 8016, max=41552, per=100.00%, avg=22467.52, stdev=5083.81, samples=373
   iops        : min= 2004, max=10388, avg=5616.87, stdev=1270.95, samples=373
  lat (usec)   : 500=67.16%, 750=29.76%, 1000=2.05%
  lat (msec)   : 2=0.60%, 4=0.24%, 10=0.05%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%, 250=0.13%, 500=0.01%
  cpu          : usr=3.59%, sys=2.66%, ctx=2097421, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=21.9MiB/s (23.0MB/s), 21.9MiB/s-21.9MiB/s (23.0MB/s-23.0MB/s), io=4096MiB (4295MB), run=186689-186689msec

Disk stats (read/write):
  sda: ios=0/1175085, merge=0/400527, ticks=0/236727, in_queue=236047, util=68.02%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 04:23 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][10.3%][r=64.3MiB/s,w=0KiB/s][r=16.4k,w=0 IOPS][eta 01m:01sJobs: 1 (f=1): [r(1)][11.8%][r=65.6MiB/s,w=0KiB/s][r=16.8k,w=0 IOPS][eta 01m:00sJobs: 1 (f=1): [r(1)][13.4%][r=62.7MiB/s,w=0KiB/s][r=16.0k,w=0 IOPS][eta 00m:58sJobs: 1 (f=1): [r(1)][14.9%][r=61.8MiB/s,w=0KiB/s][r=15.8k,w=0 IOPS][eta 00m:57sJobs: 1 (f=1): [r(1)][16.4%][r=61.6MiB/s,w=0KiB/s][r=15.8k,w=0 IOPS][eta 00m:56sJobs: 1 (f=1): [r(1)][17.9%][r=64.0MiB/s,w=0KiB/s][r=16.6k,w=0 IOPS][eta 00m:55sJobs: 1 (f=1): [r(1)][19.4%][r=61.0MiB/s,w=0KiB/s][r=15.6k,w=0 IOPS][eta 00m:54sJobs: 1 (f=1): [r(1)][21.2%][r=65.1MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [r(1)][22.1%][r=34.2MiB/s,w=0KiB/s][r=8763,w=0 IOPS][eta 00m:53s]Jobs: 1 (f=1): [r(1)][23.5%][r=57.9MiB/s,w=0KiB/s][r=14.8k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [r(1)][25.0%][r=65.4MiB/s,w=0KiB/s][r=16.8k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [r(1)][26.5%][r=58.9MiB/s,w=0KiB/s][r=15.1k,w=0 IOPS][eta 00m:50sJobs: 1 (f=1): [r(1)][27.9%][r=62.2MiB/s,w=0KiB/s][r=15.9k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [r(1)][29.4%][r=60.8MiB/s,w=0KiB/s][r=15.6k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [r(1)][30.9%][r=63.3MiB/s,w=0KiB/s][r=16.2k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [r(1)][32.4%][r=60.6MiB/s,w=0KiB/s][r=15.5k,w=0 IOPS][eta 00m:46sJobs: 1 (f=1): [r(1)][33.8%][r=57.9MiB/s,w=0KiB/s][r=14.8k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [r(1)][35.3%][r=61.4MiB/s,w=0KiB/s][r=15.7k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [r(1)][36.8%][r=57.6MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [r(1)][38.2%][r=62.5MiB/s,w=0KiB/s][r=16.0k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [r(1)][39.7%][r=63.7MiB/s,w=0KiB/s][r=16.3k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [r(1)][41.2%][r=58.6MiB/s,w=0KiB/s][r=15.0k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [r(1)][42.6%][r=59.0MiB/s,w=0KiB/s][r=15.4k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [r(1)][44.1%][r=57.2MiB/s,w=0KiB/s][r=14.6k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [r(1)][45.6%][r=58.4MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [r(1)][47.1%][r=52.6MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [r(1)][48.5%][r=57.3MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [r(1)][50.0%][r=54.8MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [r(1)][51.5%][r=55.0MiB/s,w=0KiB/s][r=14.1k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [r(1)][52.2%][r=55.2MiB/s,w=0KiB/s][r=14.1k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [r(1)][53.6%][r=48.9MiB/s,w=0KiB/s][r=12.5k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [r(1)][55.1%][r=58.6MiB/s,w=0KiB/s][r=15.0k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [r(1)][56.5%][r=54.8MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][58.0%][r=50.3MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [r(1)][58.6%][r=51.7MiB/s,w=0KiB/s][r=13.2k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [r(1)][60.9%][r=63.9MiB/s,w=0KiB/s][r=16.4k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [r(1)][62.3%][r=57.1MiB/s,w=0KiB/s][r=14.6k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [r(1)][63.8%][r=57.2MiB/s,w=0KiB/s][r=14.6k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [r(1)][64.3%][r=46.5MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [r(1)][65.7%][r=49.0MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [r(1)][67.1%][r=40.6MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [r(1)][67.6%][r=44.4MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [r(1)][69.0%][r=45.1MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [r(1)][69.4%][r=42.4MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [r(1)][70.8%][r=50.2MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [r(1)][72.2%][r=51.9MiB/s,w=0KiB/s][r=13.3k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [r(1)][73.6%][r=52.2MiB/s,w=0KiB/s][r=13.4k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [r(1)][75.0%][r=51.2MiB/s,w=0KiB/s][r=13.1k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [r(1)][76.4%][r=65.6MiB/s,w=0KiB/s][r=16.8k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [r(1)][77.8%][r=68.5MiB/s,w=0KiB/s][r=17.5k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [r(1)][79.2%][r=59.5MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [r(1)][80.6%][r=51.3MiB/s,w=0KiB/s][r=13.1k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [r(1)][81.9%][r=55.0MiB/s,w=0KiB/s][r=14.1k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [r(1)][83.3%][r=57.9MiB/s,w=0KiB/s][r=14.8k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [r(1)][84.7%][r=52.8MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [r(1)][86.1%][r=49.8MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [r(1)][87.5%][r=51.9MiB/s,w=0KiB/s][r=13.3k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [r(1)][88.9%][r=49.1MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [r(1)][90.3%][r=50.1MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [r(1)][91.7%][r=64.9MiB/s,w=0KiB/s][r=16.6k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [r(1)][93.1%][r=61.2MiB/s,w=0KiB/s][r=15.7k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [r(1)][94.4%][r=64.6MiB/s,w=0KiB/s][r=16.5k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [r(1)][95.8%][r=64.5MiB/s,w=0KiB/s][r=16.5k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [r(1)][97.2%][r=59.9MiB/s,w=0KiB/s][r=15.3k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [r(1)][98.6%][r=54.5MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [r(1)][100.0%][r=53.6MiB/s,w=0KiB/s][r=13.7k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=5540: Fri Oct  6 04:25:59 2017
   read: IOPS=14.5k, BW=56.8MiB/s (59.5MB/s)(4096MiB/72136msec)
    slat (nsec): min=200, max=131103, avg=639.72, stdev=526.89
    clat (usec): min=24, max=10453, avg=272.67, stdev=139.19
     lat (usec): min=24, max=10454, avg=273.31, stdev=139.24
    clat percentiles (usec):
     |  1.00th=[   37],  5.00th=[  109], 10.00th=[  137], 20.00th=[  182],
     | 30.00th=[  210], 40.00th=[  239], 50.00th=[  265], 60.00th=[  289],
     | 70.00th=[  318], 80.00th=[  355], 90.00th=[  408], 95.00th=[  457],
     | 99.00th=[  570], 99.50th=[  635], 99.90th=[ 1270], 99.95th=[ 2073],
     | 99.99th=[ 4228]
   bw (  KiB/s): min=32880, max=70976, per=100.00%, avg=58156.99, stdev=7512.65, samples=144
   iops        : min= 8220, max=17744, avg=14539.24, stdev=1878.16, samples=144
  lat (usec)   : 50=1.59%, 100=1.50%, 250=41.40%, 500=52.77%, 750=2.47%
  lat (usec)   : 1000=0.11%
  lat (msec)   : 2=0.09%, 4=0.04%, 10=0.01%, 20=0.01%
  cpu          : usr=6.88%, sys=4.84%, ctx=2097338, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=56.8MiB/s (59.5MB/s), 56.8MiB/s-56.8MiB/s (59.5MB/s-59.5MB/s), io=4096MiB (4295MB), run=72136-72136msec

Disk stats (read/write):
  sda: ios=660934/11, merge=0/8, ticks=38000/13, in_queue=37730, util=52.42%
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

*writes*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=22.4MiB/s][r=0,w=5730 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=17291: Fri Oct  6 04:25:17 2017
  write: IOPS=3585, BW=14.0MiB/s (14.7MB/s)(4096MiB/292467msec)
    slat (nsec): min=222, max=78864, avg=536.34, stdev=295.18
    clat (usec): min=423, max=287055, avg=1113.75, stdev=4589.33
     lat (usec): min=424, max=287056, avg=1114.29, stdev=4589.34
    clat percentiles (usec):
     |  1.00th=[   537],  5.00th=[   578], 10.00th=[   603], 20.00th=[   660],
     | 30.00th=[   791], 40.00th=[   848], 50.00th=[   922], 60.00th=[  1045],
     | 70.00th=[  1139], 80.00th=[  1287], 90.00th=[  1483], 95.00th=[  1614],
     | 99.00th=[  2474], 99.50th=[  3130], 99.90th=[  5669], 99.95th=[ 42206],
     | 99.99th=[248513]
   bw (  KiB/s): min= 5744, max=25880, per=99.92%, avg=14329.45, stdev=4099.35, samples=584
   iops        : min= 1436, max= 6470, avg=3582.36, stdev=1024.84, samples=584
  lat (usec)   : 500=0.10%, 750=25.61%, 1000=29.67%
  lat (msec)   : 2=42.61%, 4=1.76%, 10=0.19%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%, 250=0.03%, 500=0.01%
  cpu          : usr=1.11%, sys=0.73%, ctx=2097245, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=14.0MiB/s (14.7MB/s), 14.0MiB/s-14.0MiB/s (14.7MB/s-14.7MB/s), io=4096MiB (4295MB), run=292467-292467msec

Disk stats (read/write):
  vda: ios=0/1068141, merge=0/215179, ticks=0/469780, in_queue=469624, util=92.62%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 04:25 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][11.5%][r=71.2MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:54sJobs: 1 (f=1): [r(1)][13.1%][r=70.6MiB/s,w=0KiB/s][r=18.1k,w=0 IOPS][eta 00m:53sJobs: 1 (f=1): [r(1)][14.8%][r=66.0MiB/s,w=0KiB/s][r=17.1k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [r(1)][16.4%][r=65.1MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [r(1)][18.0%][r=65.8MiB/s,w=0KiB/s][r=16.8k,w=0 IOPS][eta 00m:50sJobs: 1 (f=1): [r(1)][19.7%][r=70.2MiB/s,w=0KiB/s][r=17.0k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [r(1)][21.3%][r=70.0MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [r(1)][23.0%][r=63.3MiB/s,w=0KiB/s][r=16.2k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [r(1)][24.6%][r=71.4MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:46sJobs: 1 (f=1): [r(1)][26.7%][r=70.0MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [r(1)][28.3%][r=71.6MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [r(1)][30.0%][r=70.5MiB/s,w=0KiB/s][r=18.1k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [r(1)][31.7%][r=63.9MiB/s,w=0KiB/s][r=16.4k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [r(1)][33.3%][r=59.5MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [r(1)][34.4%][r=63.5MiB/s,w=0KiB/s][r=16.3k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [r(1)][36.1%][r=68.0MiB/s,w=0KiB/s][r=17.7k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [r(1)][38.3%][r=74.4MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [r(1)][40.0%][r=66.4MiB/s,w=0KiB/s][r=16.0k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [r(1)][41.0%][r=60.8MiB/s,w=0KiB/s][r=15.6k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [r(1)][42.6%][r=62.5MiB/s,w=0KiB/s][r=16.0k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [r(1)][45.0%][r=77.0MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [r(1)][46.7%][r=76.8MiB/s,w=0KiB/s][r=19.7k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [r(1)][48.3%][r=72.6MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [r(1)][50.0%][r=72.3MiB/s,w=0KiB/s][r=18.5k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][51.7%][r=72.0MiB/s,w=0KiB/s][r=18.4k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [r(1)][53.3%][r=51.6MiB/s,w=0KiB/s][r=13.2k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [r(1)][55.0%][r=62.0MiB/s,w=0KiB/s][r=16.1k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [r(1)][56.7%][r=57.7MiB/s,w=0KiB/s][r=14.8k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [r(1)][57.4%][r=57.8MiB/s,w=0KiB/s][r=14.8k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [r(1)][59.0%][r=58.6MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [r(1)][60.7%][r=65.1MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [r(1)][62.3%][r=67.7MiB/s,w=0KiB/s][r=17.3k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [r(1)][63.9%][r=56.0MiB/s,w=0KiB/s][r=14.6k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [r(1)][65.6%][r=57.4MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [r(1)][66.1%][r=59.0MiB/s,w=0KiB/s][r=15.1k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [r(1)][67.7%][r=61.3MiB/s,w=0KiB/s][r=15.7k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [r(1)][69.4%][r=68.7MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [r(1)][71.0%][r=61.8MiB/s,w=0KiB/s][r=15.8k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [r(1)][72.6%][r=57.5MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [r(1)][74.2%][r=59.6MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [r(1)][75.8%][r=66.5MiB/s,w=0KiB/s][r=17.0k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [r(1)][77.4%][r=65.7MiB/s,w=0KiB/s][r=16.8k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [r(1)][79.0%][r=64.6MiB/s,w=0KiB/s][r=16.5k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [r(1)][80.6%][r=59.2MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [r(1)][82.3%][r=63.7MiB/s,w=0KiB/s][r=16.3k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [r(1)][83.9%][r=72.3MiB/s,w=0KiB/s][r=18.5k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [r(1)][85.5%][r=69.9MiB/s,w=0KiB/s][r=17.9k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [r(1)][87.1%][r=65.4MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [r(1)][88.7%][r=64.3MiB/s,w=0KiB/s][r=16.5k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [r(1)][90.3%][r=64.0MiB/s,w=0KiB/s][r=16.4k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [r(1)][91.9%][r=66.4MiB/s,w=0KiB/s][r=16.0k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [r(1)][93.5%][r=79.2MiB/s,w=0KiB/s][r=20.3k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [r(1)][95.2%][r=77.0MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [r(1)][96.8%][r=66.8MiB/s,w=0KiB/s][r=17.1k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [r(1)][98.4%][r=63.9MiB/s,w=0KiB/s][r=16.3k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [r(1)][100.0%][r=68.8MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=17296: Fri Oct  6 04:27:14 2017
   read: IOPS=16.9k, BW=66.1MiB/s (69.3MB/s)(4096MiB/61943msec)
    slat (nsec): min=184, max=65913, avg=290.55, stdev=186.51
    clat (usec): min=17, max=146908, avg=235.16, stdev=304.31
     lat (usec): min=18, max=146908, avg=235.45, stdev=304.32
    clat percentiles (usec):
     |  1.00th=[   21],  5.00th=[   95], 10.00th=[  110], 20.00th=[  163],
     | 30.00th=[  186], 40.00th=[  204], 50.00th=[  233], 60.00th=[  258],
     | 70.00th=[  277], 80.00th=[  306], 90.00th=[  351], 95.00th=[  383],
     | 99.00th=[  465], 99.50th=[  529], 99.90th=[  881], 99.95th=[ 1254],
     | 99.99th=[ 2114]
   bw (  KiB/s): min=48760, max=87696, per=99.89%, avg=67636.81, stdev=6645.46, samples=123
   iops        : min=12190, max=21924, avg=16909.20, stdev=1661.37, samples=123
  lat (usec)   : 20=0.41%, 50=1.45%, 100=4.93%, 250=50.74%, 500=41.83%
  lat (usec)   : 750=0.49%, 1000=0.07%
  lat (msec)   : 2=0.07%, 4=0.01%, 10=0.01%, 20=0.01%, 250=0.01%
  cpu          : usr=2.96%, sys=2.93%, ctx=2097205, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=66.1MiB/s (69.3MB/s), 66.1MiB/s-66.1MiB/s (69.3MB/s-69.3MB/s), io=4096MiB (4295MB), run=61943-61943msec

Disk stats (read/write):
  vda: ios=661439/4, merge=0/1, ticks=51852/0, in_queue=51796, util=83.57%
```

