# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G

# random reads
fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
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
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=11.8MiB/s][r=0,w=3011 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=21436: Fri Oct  6 05:08:47 2017
  write: IOPS=3065, BW=11.0MiB/s (12.6MB/s)(3593MiB/300002msec)
    slat (usec): min=2, max=54304, avg=11.11, stdev=108.42
    clat (usec): min=104, max=55295, avg=1291.82, stdev=1863.92
     lat (usec): min=374, max=55302, avg=1303.18, stdev=1867.66
    clat percentiles (usec):
     |  1.00th=[  437],  5.00th=[  478], 10.00th=[  502], 20.00th=[  553],
     | 30.00th=[  635], 40.00th=[  979], 50.00th=[ 1221], 60.00th=[ 1270],
     | 70.00th=[ 1303], 80.00th=[ 1336], 90.00th=[ 1401], 95.00th=[ 1598],
     | 99.00th=[13173], 99.50th=[13960], 99.90th=[17957], 99.95th=[21890],
     | 99.99th=[26084]
   bw (  KiB/s): min= 8968, max=23432, per=99.99%, avg=12261.73, stdev=727.40, samples=600
   iops        : min= 2242, max= 5858, avg=3065.40, stdev=181.85, samples=600
  lat (usec)   : 250=0.01%, 500=9.37%, 750=25.80%, 1000=5.16%
  lat (msec)   : 2=56.54%, 4=0.71%, 10=0.47%, 20=1.88%, 50=0.07%
  lat (msec)   : 100=0.01%
  cpu          : usr=0.69%, sys=3.96%, ctx=864419, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,919738,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=11.0MiB/s (12.6MB/s), 11.0MiB/s-11.0MiB/s (12.6MB/s-12.6MB/s), io=3593MiB (3767MB), run=300002-300002msec

Disk stats (read/write):
  xvda: ios=0/921936, merge=0/31337, ticks=0/1211900, in_queue=1211892, util=100.00%
```

*file-size*
```
ls -al test4Krandom-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:08 test4Krandom-aio
```

*reads*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=20.5MiB/s,w=0KiB/s][r=5251,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=21450: Fri Oct  6 05:14:11 2017
   read: IOPS=5269, BW=20.6MiB/s (21.6MB/s)(4096MiB/198990msec)
    slat (nsec): min=841, max=195666, avg=5250.41, stdev=2448.71
    clat (nsec): min=249, max=20808k, avg=752566.33, stdev=749893.80
     lat (nsec): min=1280, max=20814k, avg=758003.12, stdev=751397.87
    clat percentiles (nsec):
     |  1.00th=[     278],  5.00th=[     282], 10.00th=[     290],
     | 20.00th=[     354], 30.00th=[     394], 40.00th=[     564],
     | 50.00th=[ 1073152], 60.00th=[ 1187840], 70.00th=[ 1286144],
     | 80.00th=[ 1318912], 90.00th=[ 1449984], 95.00th=[ 1482752],
     | 99.00th=[ 2801664], 99.50th=[ 3850240], 99.90th=[ 6062080],
     | 99.95th=[ 7503872], 99.99th=[10682368]
   bw (  KiB/s): min=19896, max=43568, per=99.99%, avg=21075.61, stdev=1497.09, samples=397
   iops        : min= 4974, max=10892, avg=5268.88, stdev=374.28, samples=397
  lat (nsec)   : 250=0.01%, 500=37.87%, 750=2.95%, 1000=0.25%
  lat (usec)   : 2=0.01%, 4=0.11%, 10=0.34%, 20=0.10%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.31%, 500=1.55%, 750=0.94%, 1000=3.82%
  lat (msec)   : 2=50.18%, 4=1.11%, 10=0.44%, 20=0.01%, 50=0.01%
  cpu          : usr=1.04%, sys=4.06%, ctx=603432, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=20.6MiB/s (21.6MB/s), 20.6MiB/s-20.6MiB/s (21.6MB/s-21.6MB/s), io=4096MiB (4295MB), run=198990-198990msec

Disk stats (read/write):
  xvda: ios=611674/8, merge=0/2, ticks=792656/8, in_queue=792652, util=100.00%
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
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=6030KiB/s][r=0,w=1507 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2620: Fri Oct  6 05:10:11 2017
  write: IOPS=1492, BW=5970KiB/s (6114kB/s)(1749MiB/300003msec)
    slat (usec): min=5, max=205791, avg=43.74, stdev=1461.39
    clat (nsec): min=1162, max=208621k, avg=2632860.53, stdev=2710169.97
     lat (usec): min=455, max=208650, avg=2677.01, stdev=3082.18
    clat percentiles (usec):
     |  1.00th=[   594],  5.00th=[  1106], 10.00th=[  1565], 20.00th=[  2024],
     | 30.00th=[  2311], 40.00th=[  2474], 50.00th=[  2638], 60.00th=[  2769],
     | 70.00th=[  2900], 80.00th=[  3064], 90.00th=[  3458], 95.00th=[  3720],
     | 99.00th=[  5669], 99.50th=[  7177], 99.90th=[  9110], 99.95th=[ 21365],
     | 99.99th=[181404]
   bw (  KiB/s): min= 4944, max= 7920, per=100.00%, avg=5970.20, stdev=260.90, samples=600
   iops        : min= 1236, max= 1980, avg=1492.55, stdev=65.23, samples=600
  lat (usec)   : 2=0.01%, 50=0.01%, 100=0.01%, 250=0.01%, 500=0.06%
  lat (usec)   : 750=2.67%, 1000=1.33%
  lat (msec)   : 2=15.56%, 4=77.36%, 10=2.92%, 20=0.03%, 50=0.03%
  lat (msec)   : 100=0.01%, 250=0.02%
  cpu          : usr=0.85%, sys=4.11%, ctx=380997, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,447789,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=5970KiB/s (6114kB/s), 5970KiB/s-5970KiB/s (6114kB/s-6114kB/s), io=1749MiB (1834MB), run=300003-300003msec

Disk stats (read/write):
  sda: ios=196/454931, merge=0/86348, ticks=3368/1186152, in_queue=1189324, util=99.98%
```

*file-size*
```
ls -al test4Krandom-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:10 test4Krandom-aio
```

*reads*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=2896KiB/s,w=0KiB/s][r=724,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2643: Fri Oct  6 05:15:57 2017
   read: IOPS=736, BW=2946KiB/s (3017kB/s)(863MiB/300021msec)
    slat (nsec): min=1249, max=5648.6k, avg=13221.37, stdev=19107.23
    clat (nsec): min=250, max=172959k, avg=5414376.44, stdev=9397788.83
     lat (nsec): min=1604, max=172975k, avg=5427837.28, stdev=9404397.00
    clat percentiles (nsec):
     |  1.00th=[      278],  5.00th=[      290], 10.00th=[      302],
     | 20.00th=[      322], 30.00th=[      350], 40.00th=[      450],
     | 50.00th=[      796], 60.00th=[     1304], 70.00th=[  6717440],
     | 80.00th=[ 13172736], 90.00th=[ 19005440], 95.00th=[ 24248320],
     | 99.00th=[ 36438016], 99.50th=[ 42205184], 99.90th=[ 63176704],
     | 99.95th=[ 74973184], 99.99th=[123207680]
   bw (  KiB/s): min= 2168, max= 3880, per=100.00%, avg=2946.60, stdev=288.67, samples=600
   iops        : min=  542, max=  970, avg=736.65, stdev=72.17, samples=600
  lat (nsec)   : 500=40.73%, 750=7.41%, 1000=9.21%
  lat (usec)   : 2=5.27%, 4=1.21%, 10=0.89%, 20=0.22%, 50=0.30%
  lat (usec)   : 100=0.02%, 250=0.01%, 500=0.25%, 750=0.87%, 1000=0.37%
  lat (msec)   : 2=1.55%, 4=0.56%, 10=5.12%, 20=17.23%, 50=8.53%
  lat (msec)   : 100=0.24%, 250=0.02%
  cpu          : usr=0.32%, sys=1.20%, ctx=75611, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=220997,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=2946KiB/s (3017kB/s), 2946KiB/s-2946KiB/s (3017kB/s-3017kB/s), io=863MiB (905MB), run=300021-300021msec

Disk stats (read/write):
  sda: ios=76736/69, merge=0/43, ticks=1194748/308, in_queue=1195064, util=100.00%
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
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][14.3%][r=0KiB/s,w=96.0MiB/s][r=0,w=24.8k IOPS][eta 00m:36sJobs: 1 (f=1): [w(1)][17.1%][r=0KiB/s,w=107MiB/s][r=0,w=27.4k IOPS][eta 00m:34s]Jobs: 1 (f=1): [w(1)][19.5%][r=0KiB/s,w=96.4MiB/s][r=0,w=24.7k IOPS][eta 00m:33sJobs: 1 (f=1): [w(1)][22.0%][r=0KiB/s,w=95.5MiB/s][r=0,w=24.4k IOPS][eta 00m:32sJobs: 1 (f=1): [w(1)][25.0%][r=0KiB/s,w=118MiB/s][r=0,w=30.2k IOPS][eta 00m:30s]Jobs: 1 (f=1): [w(1)][32.5%][r=0KiB/s,w=98.0MiB/s][r=0,w=25.1k IOPS][eta 00m:27sJobs: 1 (f=1): [w(1)][35.0%][r=0KiB/s,w=107MiB/s][r=0,w=27.3k IOPS][eta 00m:26s]Jobs: 1 (f=1): [w(1)][47.5%][r=0KiB/s,w=99.8MiB/s][r=0,w=25.6k IOPS][eta 00m:21sJobs: 1 (f=1): [w(1)][50.0%][r=0KiB/s,w=102MiB/s][r=0,w=26.1k IOPS][eta 00m:20s]Jobs: 1 (f=1): [w(1)][69.2%][r=0KiB/s,w=97.3MiB/s][r=0,w=24.9k IOPS][eta 00m:12sJobs: 1 (f=1): [w(1)][71.8%][r=0KiB/s,w=102MiB/s][r=0,w=26.1k IOPS][eta 00m:11s]Jobs: 1 (f=1): [w(1)][79.5%][r=0KiB/s,w=99.8MiB/s][r=0,w=25.6k IOPS][eta 00m:08sJobs: 1 (f=1): [w(1)][82.1%][r=0KiB/s,w=108MiB/s][r=0,w=27.6k IOPS][eta 00m:07s]Jobs: 1 (f=1): [w(1)][97.4%][r=0KiB/s,w=99.3MiB/s][r=0,w=25.4k IOPS][eta 00m:01sJobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=112MiB/s][r=0,w=28.6k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14241: Fri Oct  6 05:06:38 2017
  write: IOPS=26.9k, BW=105MiB/s (110MB/s)(4096MiB/39020msec)
    slat (usec): min=2, max=45930, avg=15.97, stdev=83.85
    clat (usec): min=17, max=50224, avg=130.56, stdev=187.55
     lat (usec): min=47, max=50248, avg=146.99, stdev=209.67
    clat percentiles (usec):
     |  1.00th=[   57],  5.00th=[   67], 10.00th=[   73], 20.00th=[   84],
     | 30.00th=[   93], 40.00th=[  103], 50.00th=[  115], 60.00th=[  128],
     | 70.00th=[  143], 80.00th=[  163], 90.00th=[  202], 95.00th=[  247],
     | 99.00th=[  343], 99.50th=[  392], 99.90th=[  676], 99.95th=[ 1090],
     | 99.99th=[ 3032]
   bw (  KiB/s): min=86768, max=127040, per=100.00%, avg=107488.22, stdev=9232.14, samples=78
   iops        : min=21692, max=31760, avg=26872.05, stdev=2308.03, samples=78
  lat (usec)   : 20=0.01%, 50=0.20%, 100=37.21%, 250=57.77%, 500=4.64%
  lat (usec)   : 750=0.09%, 1000=0.03%
  lat (msec)   : 2=0.04%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%
  cpu          : usr=6.45%, sys=40.56%, ctx=638332, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=105MiB/s (110MB/s), 105MiB/s-105MiB/s (110MB/s-110MB/s), io=4096MiB (4295MB), run=39020-39020msec

Disk stats (read/write):
  vda: ios=12/1046077, merge=0/18790, ticks=0/118872, in_queue=118632, util=95.53%
```

*file-size*
```
ls -al test4Krandom-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:06 test4Krandom-aio
```

*reads*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][19.5%][r=96.5MiB/s,w=0KiB/s][r=24.7k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [r(1)][22.5%][r=117MiB/s,w=0KiB/s][r=29.9k,w=0 IOPS][eta 00m:31s]Jobs: 1 (f=1): [r(1)][25.0%][r=97.1MiB/s,w=0KiB/s][r=24.9k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][26.8%][r=77.8MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][28.6%][r=70.0MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][31.0%][r=83.6MiB/s,w=0KiB/s][r=21.4k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [r(1)][32.6%][r=91.3MiB/s,w=0KiB/s][r=23.4k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [r(1)][35.7%][r=105MiB/s,w=0KiB/s][r=26.8k,w=0 IOPS][eta 00m:27s]Jobs: 1 (f=1): [r(1)][38.1%][r=98.2MiB/s,w=0KiB/s][r=25.1k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [r(1)][40.5%][r=108MiB/s,w=0KiB/s][r=27.6k,w=0 IOPS][eta 00m:25s]Jobs: 1 (f=1): [r(1)][65.0%][r=97.0MiB/s,w=0KiB/s][r=24.8k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [r(1)][67.5%][r=102MiB/s,w=0KiB/s][r=26.2k,w=0 IOPS][eta 00m:13s]Jobs: 1 (f=1): [r(1)][75.0%][r=97.9MiB/s,w=0KiB/s][r=25.1k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [r(1)][77.5%][r=103MiB/s,w=0KiB/s][r=26.4k,w=0 IOPS][eta 00m:09s]Jobs: 1 (f=1): [r(1)][90.0%][r=97.9MiB/s,w=0KiB/s][r=25.1k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [r(1)][92.5%][r=105MiB/s,w=0KiB/s][r=26.0k,w=0 IOPS][eta 00m:03s]Jobs: 1 (f=1): [r(1)][100.0%][r=91.9MiB/s,w=0KiB/s][r=23.5k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14261: Fri Oct  6 05:11:42 2017
   read: IOPS=26.0k, BW=102MiB/s (107MB/s)(4096MiB/40256msec)
    slat (nsec): min=987, max=18597k, avg=8826.40, stdev=20140.21
    clat (nsec): min=254, max=45910k, avg=142658.91, stdev=338975.92
     lat (nsec): min=1479, max=45970k, avg=151931.67, stdev=340548.12
    clat percentiles (nsec):
     |  1.00th=[     314],  5.00th=[     510], 10.00th=[     604],
     | 20.00th=[    1020], 30.00th=[   14272], 40.00th=[  148480],
     | 50.00th=[  166912], 60.00th=[  181248], 70.00th=[  193536],
     | 80.00th=[  211968], 90.00th=[  246784], 95.00th=[  288768],
     | 99.00th=[  561152], 99.50th=[  806912], 99.90th=[ 1630208],
     | 99.95th=[ 2146304], 99.99th=[17956864]
   bw (  KiB/s): min=70400, max=124232, per=99.97%, avg=104159.83, stdev=10702.46, samples=80
   iops        : min=17600, max=31058, avg=26039.95, stdev=2675.61, samples=80
  lat (nsec)   : 500=4.73%, 750=13.05%, 1000=2.00%
  lat (usec)   : 2=1.30%, 4=0.17%, 10=4.60%, 20=6.91%, 50=3.80%
  lat (usec)   : 100=0.25%, 250=53.75%, 500=8.31%, 750=0.54%, 1000=0.33%
  lat (msec)   : 2=0.21%, 4=0.03%, 10=0.01%, 20=0.01%, 50=0.01%
  cpu          : usr=6.46%, sys=29.43%, ctx=359470, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=102MiB/s (107MB/s), 102MiB/s-102MiB/s (107MB/s-107MB/s), io=4096MiB (4295MB), run=40256-40256msec

Disk stats (read/write):
  vda: ios=660302/6, merge=0/1, ticks=137900/0, in_queue=137768, util=97.91%
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
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][10.8%][r=0KiB/s,w=49.6MiB/s][r=0,w=12.7k IOPS][eta 01m:06sJobs: 1 (f=1): [w(1)][11.5%][r=0KiB/s,w=29.8MiB/s][r=0,w=7635 IOPS][eta 01m:09s]Jobs: 1 (f=1): [w(1)][16.9%][r=0KiB/s,w=39.1MiB/s][r=0,w=10.0k IOPS][eta 01m:14sJobs: 1 (f=1): [w(1)][17.8%][r=0KiB/s,w=41.6MiB/s][r=0,w=10.7k IOPS][eta 01m:14sJobs: 1 (f=1): [w(1)][18.7%][r=0KiB/s,w=33.3MiB/s][r=0,w=8525 IOPS][eta 01m:14s]Jobs: 1 (f=1): [w(1)][36.2%][r=0KiB/s,w=44.2MiB/s][r=0,w=11.3k IOPS][eta 01m:07sJobs: 1 (f=1): [w(1)][37.1%][r=0KiB/s,w=45.0MiB/s][r=0,w=11.8k IOPS][eta 01m:06sJobs: 1 (f=1): [w(1)][38.1%][r=0KiB/s,w=38.8MiB/s][r=0,w=9924 IOPS][eta 01m:05s]Jobs: 1 (f=1): [w(1)][39.4%][r=0KiB/s,w=45.1MiB/s][r=0,w=11.5k IOPS][eta 01m:03sJobs: 1 (f=1): [w(1)][40.0%][r=0KiB/s,w=32.3MiB/s][r=0,w=8280 IOPS][eta 01m:03s]Jobs: 1 (f=1): [w(1)][44.3%][r=0KiB/s,w=39.7MiB/s][r=0,w=10.2k IOPS][eta 00m:59sJobs: 1 (f=1): [w(1)][45.3%][r=0KiB/s,w=38.2MiB/s][r=0,w=9773 IOPS][eta 00m:58s]Jobs: 1 (f=1): [w(1)][50.0%][r=0KiB/s,w=44.1MiB/s][r=0,w=11.3k IOPS][eta 00m:54sJobs: 1 (f=1): [w(1)][50.9%][r=0KiB/s,w=39.4MiB/s][r=0,w=10.1k IOPS][eta 00m:53sJobs: 1 (f=1): [w(1)][52.3%][r=0KiB/s,w=42.2MiB/s][r=0,w=10.8k IOPS][eta 00m:51sJobs: 1 (f=1): [w(1)][52.8%][r=0KiB/s,w=33.9MiB/s][r=0,w=8680 IOPS][eta 00m:51s]Jobs: 1 (f=1): [w(1)][54.2%][r=0KiB/s,w=39.7MiB/s][r=0,w=10.2k IOPS][eta 00m:49sJobs: 1 (f=1): [w(1)][55.1%][r=0KiB/s,w=47.8MiB/s][r=0,w=12.2k IOPS][eta 00m:48sJobs: 1 (f=1): [w(1)][56.1%][r=0KiB/s,w=44.9MiB/s][r=0,w=11.5k IOPS][eta 00m:47sJobs: 1 (f=1): [w(1)][57.0%][r=0KiB/s,w=35.5MiB/s][r=0,w=9083 IOPS][eta 00m:46s]Jobs: 1 (f=1): [w(1)][59.8%][r=0KiB/s,w=44.8MiB/s][r=0,w=11.5k IOPS][eta 00m:43sJobs: 1 (f=1): [w(1)][60.7%][r=0KiB/s,w=36.2MiB/s][r=0,w=9262 IOPS][eta 00m:42s]Jobs: 1 (f=1): [w(1)][67.6%][r=0KiB/s,w=40.1MiB/s][r=0,w=10.3k IOPS][eta 00m:35sJobs: 1 (f=1): [w(1)][68.5%][r=0KiB/s,w=43.1MiB/s][r=0,w=11.0k IOPS][eta 00m:34sJobs: 1 (f=1): [w(1)][69.4%][r=0KiB/s,w=40.9MiB/s][r=0,w=10.5k IOPS][eta 00m:33sJobs: 1 (f=1): [w(1)][70.4%][r=0KiB/s,w=38.9MiB/s][r=0,w=9948 IOPS][eta 00m:32s]Jobs: 1 (f=1): [w(1)][71.3%][r=0KiB/s,w=40.9MiB/s][r=0,w=10.5k IOPS][eta 00m:31sJobs: 1 (f=1): [w(1)][72.9%][r=0KiB/s,w=42.1MiB/s][r=0,w=10.8k IOPS][eta 00m:29sJobs: 1 (f=1): [w(1)][73.8%][r=0KiB/s,w=38.4MiB/s][r=0,w=9829 IOPS][eta 00m:28s]Jobs: 1 (f=1): [w(1)][78.7%][r=0KiB/s,w=41.4MiB/s][r=0,w=10.6k IOPS][eta 00m:23sJobs: 1 (f=1): [w(1)][79.6%][r=0KiB/s,w=34.5MiB/s][r=0,w=8831 IOPS][eta 00m:22s]Jobs: 1 (f=1): [w(1)][83.3%][r=0KiB/s,w=41.0MiB/s][r=0,w=10.7k IOPS][eta 00m:18sJobs: 1 (f=1): [w(1)][84.3%][r=0KiB/s,w=34.7MiB/s][r=0,w=8881 IOPS][eta 00m:17s]Jobs: 1 (f=1): [w(1)][85.2%][r=0KiB/s,w=47.1MiB/s][r=0,w=12.1k IOPS][eta 00m:16sJobs: 1 (f=1): [w(1)][86.1%][r=0KiB/s,w=35.6MiB/s][r=0,w=9102 IOPS][eta 00m:15s]Jobs: 1 (f=1): [w(1)][90.7%][r=0KiB/s,w=49.3MiB/s][r=0,w=12.6k IOPS][eta 00m:10sJobs: 1 (f=1): [w(1)][91.7%][r=0KiB/s,w=37.6MiB/s][r=0,w=9619 IOPS][eta 00m:09s]Jobs: 1 (f=1): [w(1)][96.3%][r=0KiB/s,w=52.2MiB/s][r=0,w=13.4k IOPS][eta 00m:04sJobs: 1 (f=1): [w(1)][97.2%][r=0KiB/s,w=47.2MiB/s][r=0,w=12.1k IOPS][eta 00m:03sJobs: 1 (f=1): [w(1)][97.2%][r=0KiB/s,w=19.1MiB/s][r=0,w=4878 IOPS][eta 00m:03s]Jobs: 1 (f=1): [w(1)][99.1%][r=0KiB/s,w=43.4MiB/s][r=0,w=11.1k IOPS][eta 00m:01sJobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=40.2MiB/s][r=0,w=10.3k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=13965: Fri Oct  6 05:08:09 2017
  write: IOPS=9701, BW=37.9MiB/s (39.7MB/s)(4096MiB/108087msec)
    slat (usec): min=2, max=2654.3k, avg=89.58, stdev=3950.20
    clat (nsec): min=720, max=2857.5M, avg=318210.98, stdev=7040570.74
     lat (usec): min=49, max=2857.5k, avg=408.89, stdev=8075.89
    clat percentiles (usec):
     |  1.00th=[    38],  5.00th=[    78], 10.00th=[    93], 20.00th=[   108],
     | 30.00th=[   120], 40.00th=[   130], 50.00th=[   141], 60.00th=[   153],
     | 70.00th=[   167], 80.00th=[   186], 90.00th=[   215], 95.00th=[   239],
     | 99.00th=[   302], 99.50th=[   334], 99.90th=[ 88605], 99.95th=[141558],
     | 99.99th=[214959]
   bw (  KiB/s): min=15352, max=100592, per=100.00%, avg=39937.44, stdev=13763.74, samples=210
   iops        : min= 3838, max=25148, avg=9984.34, stdev=3440.94, samples=210
  lat (nsec)   : 750=0.01%, 1000=0.03%
  lat (usec)   : 2=0.04%, 4=0.01%, 10=0.01%, 20=0.09%, 50=2.16%
  lat (usec)   : 100=11.93%, 250=82.05%, 500=3.51%, 750=0.03%, 1000=0.01%
  lat (msec)   : 2=0.03%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%, 250=0.09%, 500=0.01%, 750=0.01%, >=2000=0.01%
  cpu          : usr=2.58%, sys=28.90%, ctx=449651, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=37.9MiB/s (39.7MB/s), 37.9MiB/s-37.9MiB/s (39.7MB/s-39.7MB/s), io=4096MiB (4295MB), run=108087-108087msec

Disk stats (read/write):
  sda: ios=0/1170881, merge=0/398370, ticks=0/222493, in_queue=221737, util=91.44%
```

*file-size*
```
ls -al test4Krandom-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:08 test4Krandom-aio
```

*reads*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=206MiB/s,w=0KiB/s][r=52.8k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=13978: Fri Oct  6 05:11:27 2017
   read: IOPS=47.5k, BW=186MiB/s (195MB/s)(4096MiB/22076msec)
    slat (nsec): min=941, max=4010.3k, avg=12791.40, stdev=18694.77
    clat (nsec): min=264, max=5728.1k, avg=68620.06, stdev=59742.21
     lat (nsec): min=1358, max=5784.2k, avg=82046.70, stdev=64228.50
    clat percentiles (nsec):
     |  1.00th=[    278],  5.00th=[   4048], 10.00th=[   9280],
     | 20.00th=[  22144], 30.00th=[  39168], 40.00th=[  67072],
     | 50.00th=[  75264], 60.00th=[  81408], 70.00th=[  88576],
     | 80.00th=[  98816], 90.00th=[ 116224], 95.00th=[ 132096],
     | 99.00th=[ 171008], 99.50th=[ 195584], 99.90th=[ 354304],
     | 99.95th=[ 577536], 99.99th=[2088960]
   bw (  KiB/s): min=141056, max=233784, per=100.00%, avg=189991.64, stdev=22806.29, samples=44
   iops        : min=35264, max=58446, avg=47497.91, stdev=5701.57, samples=44
  lat (nsec)   : 500=3.92%, 750=0.14%, 1000=0.07%
  lat (usec)   : 2=0.03%, 4=0.79%, 10=5.44%, 20=7.78%, 50=14.10%
  lat (usec)   : 100=48.57%, 250=18.94%, 500=0.15%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.02%, 4=0.01%, 10=0.01%
  cpu          : usr=7.38%, sys=66.63%, ctx=208299, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=186MiB/s (195MB/s), 186MiB/s-186MiB/s (195MB/s-195MB/s), io=4096MiB (4295MB), run=22076-22076msec

Disk stats (read/write):
  sda: ios=656084/0, merge=0/0, ticks=37860/0, in_queue=37650, util=74.93%
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
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][10.7%][r=0KiB/s,w=46.6MiB/s][r=0,w=11.9k IOPS][eta 01m:15sJobs: 1 (f=1): [w(1)][12.2%][r=0KiB/s,w=60.6MiB/s][r=0,w=15.5k IOPS][eta 01m:12sJobs: 1 (f=1): [w(1)][13.8%][r=0KiB/s,w=62.8MiB/s][r=0,w=16.1k IOPS][eta 01m:09sJobs: 1 (f=1): [w(1)][15.0%][r=0KiB/s,w=51.6MiB/s][r=0,w=13.2k IOPS][eta 01m:08sJobs: 1 (f=1): [w(1)][16.5%][r=0KiB/s,w=59.9MiB/s][r=0,w=15.3k IOPS][eta 01m:06sJobs: 1 (f=1): [w(1)][17.9%][r=0KiB/s,w=64.1MiB/s][r=0,w=16.4k IOPS][eta 01m:04sJobs: 1 (f=1): [w(1)][19.7%][r=0KiB/s,w=74.6MiB/s][r=0,w=19.1k IOPS][eta 01m:01sJobs: 1 (f=1): [w(1)][21.6%][r=0KiB/s,w=71.5MiB/s][r=0,w=18.3k IOPS][eta 00m:58sJobs: 1 (f=1): [w(1)][22.7%][r=0KiB/s,w=45.3MiB/s][r=0,w=11.6k IOPS][eta 00m:58sJobs: 1 (f=1): [w(1)][23.4%][r=0KiB/s,w=33.1MiB/s][r=0,w=8478 IOPS][eta 00m:59s]Jobs: 1 (f=1): [w(1)][25.0%][r=0KiB/s,w=62.6MiB/s][r=0,w=16.0k IOPS][eta 00m:57sJobs: 1 (f=1): [w(1)][26.7%][r=0KiB/s,w=66.0MiB/s][r=0,w=16.9k IOPS][eta 00m:55sJobs: 1 (f=1): [w(1)][28.0%][r=0KiB/s,w=58.4MiB/s][r=0,w=14.9k IOPS][eta 00m:54sJobs: 1 (f=1): [w(1)][29.3%][r=0KiB/s,w=48.7MiB/s][r=0,w=12.5k IOPS][eta 00m:53sJobs: 1 (f=1): [w(1)][30.3%][r=0KiB/s,w=42.6MiB/s][r=0,w=10.9k IOPS][eta 00m:53sJobs: 1 (f=1): [w(1)][31.2%][r=0KiB/s,w=42.4MiB/s][r=0,w=10.9k IOPS][eta 00m:53sJobs: 1 (f=1): [w(1)][32.5%][r=0KiB/s,w=49.5MiB/s][r=0,w=12.7k IOPS][eta 00m:52sJobs: 1 (f=1): [w(1)][33.8%][r=0KiB/s,w=51.4MiB/s][r=0,w=13.1k IOPS][eta 00m:51sJobs: 1 (f=1): [w(1)][34.6%][r=0KiB/s,w=36.7MiB/s][r=0,w=9399 IOPS][eta 00m:51s]Jobs: 1 (f=1): [w(1)][35.9%][r=0KiB/s,w=49.7MiB/s][r=0,w=12.7k IOPS][eta 00m:50sJobs: 1 (f=1): [w(1)][36.7%][r=0KiB/s,w=46.2MiB/s][r=0,w=11.8k IOPS][eta 00m:50sJobs: 1 (f=1): [w(1)][38.0%][r=0KiB/s,w=51.0MiB/s][r=0,w=13.3k IOPS][eta 00m:49sJobs: 1 (f=1): [w(1)][39.2%][r=0KiB/s,w=37.7MiB/s][r=0,w=9649 IOPS][eta 00m:48s]Jobs: 1 (f=1): [w(1)][40.0%][r=0KiB/s,w=48.7MiB/s][r=0,w=12.5k IOPS][eta 00m:48sJobs: 1 (f=1): [w(1)][41.2%][r=0KiB/s,w=43.5MiB/s][r=0,w=11.1k IOPS][eta 00m:47sJobs: 1 (f=1): [w(1)][42.5%][r=0KiB/s,w=50.4MiB/s][r=0,w=12.9k IOPS][eta 00m:46sJobs: 1 (f=1): [w(1)][43.8%][r=0KiB/s,w=41.8MiB/s][r=0,w=10.7k IOPS][eta 00m:45sJobs: 1 (f=1): [w(1)][44.4%][r=0KiB/s,w=42.0MiB/s][r=0,w=11.0k IOPS][eta 00m:45sJobs: 1 (f=1): [w(1)][45.7%][r=0KiB/s,w=55.8MiB/s][r=0,w=14.3k IOPS][eta 00m:44sJobs: 1 (f=1): [w(1)][46.9%][r=0KiB/s,w=37.9MiB/s][r=0,w=9710 IOPS][eta 00m:43s]Jobs: 1 (f=1): [w(1)][48.1%][r=0KiB/s,w=47.2MiB/s][r=0,w=12.1k IOPS][eta 00m:42sJobs: 1 (f=1): [w(1)][49.4%][r=0KiB/s,w=54.5MiB/s][r=0,w=13.9k IOPS][eta 00m:41sJobs: 1 (f=1): [w(1)][50.6%][r=0KiB/s,w=50.0MiB/s][r=0,w=12.8k IOPS][eta 00m:40sJobs: 1 (f=1): [w(1)][51.2%][r=0KiB/s,w=41.2MiB/s][r=0,w=10.5k IOPS][eta 00m:40sJobs: 1 (f=1): [w(1)][52.4%][r=0KiB/s,w=51.4MiB/s][r=0,w=13.2k IOPS][eta 00m:39sJobs: 1 (f=1): [w(1)][54.3%][r=0KiB/s,w=54.7MiB/s][r=0,w=14.0k IOPS][eta 00m:37sJobs: 1 (f=1): [w(1)][54.9%][r=0KiB/s,w=45.3MiB/s][r=0,w=11.6k IOPS][eta 00m:37sJobs: 1 (f=1): [w(1)][56.1%][r=0KiB/s,w=41.0MiB/s][r=0,w=10.7k IOPS][eta 00m:36sJobs: 1 (f=1): [w(1)][57.3%][r=0KiB/s,w=56.4MiB/s][r=0,w=14.4k IOPS][eta 00m:35sJobs: 1 (f=1): [w(1)][58.5%][r=0KiB/s,w=42.6MiB/s][r=0,w=10.9k IOPS][eta 00m:34sJobs: 1 (f=1): [w(1)][59.8%][r=0KiB/s,w=51.1MiB/s][r=0,w=13.1k IOPS][eta 00m:33sJobs: 1 (f=1): [w(1)][61.0%][r=0KiB/s,w=53.2MiB/s][r=0,w=13.6k IOPS][eta 00m:32sJobs: 1 (f=1): [w(1)][62.2%][r=0KiB/s,w=53.4MiB/s][r=0,w=13.7k IOPS][eta 00m:31sJobs: 1 (f=1): [w(1)][63.4%][r=0KiB/s,w=35.2MiB/s][r=0,w=9008 IOPS][eta 00m:30s]Jobs: 1 (f=1): [w(1)][64.6%][r=0KiB/s,w=59.3MiB/s][r=0,w=15.2k IOPS][eta 00m:29sJobs: 1 (f=1): [w(1)][65.1%][r=0KiB/s,w=47.8MiB/s][r=0,w=12.2k IOPS][eta 00m:29sJobs: 1 (f=1): [w(1)][67.1%][r=0KiB/s,w=44.4MiB/s][r=0,w=11.4k IOPS][eta 00m:27sJobs: 1 (f=1): [w(1)][68.3%][r=0KiB/s,w=62.2MiB/s][r=0,w=15.9k IOPS][eta 00m:26sJobs: 1 (f=1): [w(1)][69.5%][r=0KiB/s,w=47.0MiB/s][r=0,w=12.0k IOPS][eta 00m:25sJobs: 1 (f=1): [w(1)][70.7%][r=0KiB/s,w=46.2MiB/s][r=0,w=11.8k IOPS][eta 00m:24sJobs: 1 (f=1): [w(1)][72.0%][r=0KiB/s,w=63.8MiB/s][r=0,w=16.3k IOPS][eta 00m:23sJobs: 1 (f=1): [w(1)][73.2%][r=0KiB/s,w=48.4MiB/s][r=0,w=12.4k IOPS][eta 00m:22sJobs: 1 (f=1): [w(1)][74.4%][r=0KiB/s,w=49.5MiB/s][r=0,w=12.7k IOPS][eta 00m:21sJobs: 1 (f=1): [w(1)][76.5%][r=0KiB/s,w=65.8MiB/s][r=0,w=16.9k IOPS][eta 00m:19sJobs: 1 (f=1): [w(1)][77.8%][r=0KiB/s,w=47.7MiB/s][r=0,w=12.2k IOPS][eta 00m:18sJobs: 1 (f=1): [w(1)][79.0%][r=0KiB/s,w=55.2MiB/s][r=0,w=14.1k IOPS][eta 00m:17sJobs: 1 (f=1): [w(1)][80.2%][r=0KiB/s,w=49.0MiB/s][r=0,w=12.8k IOPS][eta 00m:16sJobs: 1 (f=1): [w(1)][81.5%][r=0KiB/s,w=56.8MiB/s][r=0,w=14.5k IOPS][eta 00m:15sJobs: 1 (f=1): [w(1)][82.7%][r=0KiB/s,w=60.2MiB/s][r=0,w=15.4k IOPS][eta 00m:14sJobs: 1 (f=1): [w(1)][84.0%][r=0KiB/s,w=49.2MiB/s][r=0,w=12.6k IOPS][eta 00m:13sJobs: 1 (f=1): [w(1)][85.2%][r=0KiB/s,w=48.7MiB/s][r=0,w=12.5k IOPS][eta 00m:12sJobs: 1 (f=1): [w(1)][86.4%][r=0KiB/s,w=64.3MiB/s][r=0,w=16.5k IOPS][eta 00m:11sJobs: 1 (f=1): [w(1)][88.8%][r=0KiB/s,w=63.4MiB/s][r=0,w=16.2k IOPS][eta 00m:09sJobs: 1 (f=1): [w(1)][90.0%][r=0KiB/s,w=52.6MiB/s][r=0,w=13.5k IOPS][eta 00m:08sJobs: 1 (f=1): [w(1)][91.2%][r=0KiB/s,w=57.4MiB/s][r=0,w=14.7k IOPS][eta 00m:07sJobs: 1 (f=1): [w(1)][92.5%][r=0KiB/s,w=61.9MiB/s][r=0,w=15.8k IOPS][eta 00m:06sJobs: 1 (f=1): [w(1)][93.8%][r=0KiB/s,w=73.2MiB/s][r=0,w=18.7k IOPS][eta 00m:05sJobs: 1 (f=1): [w(1)][95.0%][r=0KiB/s,w=50.3MiB/s][r=0,w=12.9k IOPS][eta 00m:04sJobs: 1 (f=1): [w(1)][97.5%][r=0KiB/s,w=61.0MiB/s][r=0,w=15.9k IOPS][eta 00m:02sJobs: 1 (f=1): [w(1)][98.7%][r=0KiB/s,w=58.7MiB/s][r=0,w=15.0k IOPS][eta 00m:01sJobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=62.1MiB/s][r=0,w=15.9k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19038: Fri Oct  6 05:07:52 2017
  write: IOPS=13.3k, BW=52.1MiB/s (54.6MB/s)(4096MiB/78597msec)
    slat (nsec): min=1771, max=278521k, avg=23504.03, stdev=1838370.29
    clat (usec): min=26, max=523208, avg=275.21, stdev=4035.83
     lat (usec): min=71, max=523215, avg=298.91, stdev=4458.20
    clat percentiles (usec):
     |  1.00th=[    93],  5.00th=[   110], 10.00th=[   119], 20.00th=[   129],
     | 30.00th=[   137], 40.00th=[   143], 50.00th=[   153], 60.00th=[   165],
     | 70.00th=[   229], 80.00th=[   273], 90.00th=[   338], 95.00th=[   371],
     | 99.00th=[   693], 99.50th=[  1254], 99.90th=[  2212], 99.95th=[  2769],
     | 99.99th=[240124]
   bw (  KiB/s): min=18304, max=85584, per=99.90%, avg=53309.22, stdev=12861.95, samples=157
   iops        : min= 4576, max=21396, avg=13327.31, stdev=3215.49, samples=157
  lat (usec)   : 50=0.01%, 100=2.21%, 250=73.01%, 500=22.97%, 750=0.88%
  lat (usec)   : 1000=0.23%
  lat (msec)   : 2=0.55%, 4=0.11%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%, 250=0.02%, 500=0.01%, 750=0.01%
  cpu          : usr=1.96%, sys=11.65%, ctx=793531, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=52.1MiB/s (54.6MB/s), 52.1MiB/s-52.1MiB/s (54.6MB/s-54.6MB/s), io=4096MiB (4295MB), run=78597-78597msec

Disk stats (read/write):
  vda: ios=0/1062477, merge=0/193410, ticks=0/409688, in_queue=409600, util=99.71%
```

*file-size*
```
ls -al test4Krandom-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:07 test4Krandom-aio
```

*reads*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=310MiB/s,w=0KiB/s][r=79.4k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19055: Fri Oct  6 05:11:21 2017
   read: IOPS=80.7k, BW=315MiB/s (331MB/s)(4096MiB/12995msec)
    slat (nsec): min=771, max=192500, avg=3367.35, stdev=1626.64
    clat (nsec): min=270, max=1507.1k, avg=45425.69, stdev=36595.14
     lat (nsec): min=1200, max=1509.6k, avg=48944.46, stdev=37432.83
    clat percentiles (nsec):
     |  1.00th=[   282],  5.00th=[   286], 10.00th=[   290], 20.00th=[  2608],
     | 30.00th=[  5792], 40.00th=[ 49920], 50.00th=[ 59136], 60.00th=[ 64256],
     | 70.00th=[ 68096], 80.00th=[ 73216], 90.00th=[ 81408], 95.00th=[ 88576],
     | 99.00th=[110080], 99.50th=[146432], 99.90th=[244736], 99.95th=[276480],
     | 99.99th=[561152]
   bw (  KiB/s): min=281440, max=350992, per=100.00%, avg=323030.40, stdev=16074.92, samples=25
   iops        : min=70360, max=87748, avg=80757.60, stdev=4018.73, samples=25
  lat (nsec)   : 500=19.31%, 750=0.05%, 1000=0.01%
  lat (usec)   : 2=0.10%, 4=4.51%, 10=11.31%, 20=1.41%, 50=3.39%
  lat (usec)   : 100=58.00%, 250=1.83%, 500=0.08%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%
  cpu          : usr=7.45%, sys=34.85%, ctx=337045, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=315MiB/s (331MB/s), 315MiB/s-315MiB/s (331MB/s-331MB/s), io=4096MiB (4295MB), run=12995-12995msec

Disk stats (read/write):
  vda: ios=658624/7, merge=0/1, ticks=43732/0, in_queue=43660, util=98.81%
```

## ovh sg - 1024M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            476M     0  476M   0% /dev
tmpfs            97M  3.0M   94M   4% /run
/dev/sda1        30G  1.5G   28G   6% /
tmpfs           485M     0  485M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           485M     0  485M   0% /sys/fs/cgroup
tmpfs            97M     0   97M   0% /run/user/901
```

*writes*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][10.4%][r=0KiB/s,w=81.7MiB/s][r=0,w=20.9k IOPS][eta 00m:43sJobs: 1 (f=1): [w(1)][12.5%][r=0KiB/s,w=86.4MiB/s][r=0,w=22.1k IOPS][eta 00m:42sJobs: 1 (f=1): [w(1)][14.6%][r=0KiB/s,w=82.0MiB/s][r=0,w=21.0k IOPS][eta 00m:41sJobs: 1 (f=1): [w(1)][16.7%][r=0KiB/s,w=87.4MiB/s][r=0,w=22.4k IOPS][eta 00m:40sJobs: 1 (f=1): [w(1)][19.1%][r=0KiB/s,w=90.1MiB/s][r=0,w=23.1k IOPS][eta 00m:38sJobs: 1 (f=1): [w(1)][20.8%][r=0KiB/s,w=82.1MiB/s][r=0,w=21.0k IOPS][eta 00m:38sJobs: 1 (f=1): [w(1)][22.9%][r=0KiB/s,w=75.6MiB/s][r=0,w=19.3k IOPS][eta 00m:37sJobs: 1 (f=1): [w(1)][25.0%][r=0KiB/s,w=86.1MiB/s][r=0,w=22.0k IOPS][eta 00m:36sJobs: 1 (f=1): [w(1)][27.1%][r=0KiB/s,w=89.4MiB/s][r=0,w=22.9k IOPS][eta 00m:35sJobs: 1 (f=1): [w(1)][29.2%][r=0KiB/s,w=89.4MiB/s][r=0,w=22.9k IOPS][eta 00m:34sJobs: 1 (f=1): [w(1)][31.2%][r=0KiB/s,w=86.6MiB/s][r=0,w=22.2k IOPS][eta 00m:33sJobs: 1 (f=1): [w(1)][33.3%][r=0KiB/s,w=87.3MiB/s][r=0,w=22.4k IOPS][eta 00m:32sJobs: 1 (f=1): [w(1)][35.4%][r=0KiB/s,w=85.7MiB/s][r=0,w=21.9k IOPS][eta 00m:31sJobs: 1 (f=1): [w(1)][38.3%][r=0KiB/s,w=91.1MiB/s][r=0,w=23.3k IOPS][eta 00m:29sJobs: 1 (f=1): [w(1)][40.4%][r=0KiB/s,w=85.9MiB/s][r=0,w=21.0k IOPS][eta 00m:28sJobs: 1 (f=1): [w(1)][42.6%][r=0KiB/s,w=85.4MiB/s][r=0,w=21.9k IOPS][eta 00m:27sJobs: 1 (f=1): [w(1)][44.7%][r=0KiB/s,w=83.9MiB/s][r=0,w=21.5k IOPS][eta 00m:26sJobs: 1 (f=1): [w(1)][46.8%][r=0KiB/s,w=85.4MiB/s][r=0,w=21.9k IOPS][eta 00m:25sJobs: 1 (f=1): [w(1)][48.9%][r=0KiB/s,w=86.9MiB/s][r=0,w=22.3k IOPS][eta 00m:24sJobs: 1 (f=1): [w(1)][51.1%][r=0KiB/s,w=87.4MiB/s][r=0,w=22.4k IOPS][eta 00m:23sJobs: 1 (f=1): [w(1)][53.2%][r=0KiB/s,w=82.7MiB/s][r=0,w=21.2k IOPS][eta 00m:22sJobs: 1 (f=1): [w(1)][55.3%][r=0KiB/s,w=87.2MiB/s][r=0,w=22.3k IOPS][eta 00m:21sJobs: 1 (f=1): [w(1)][57.4%][r=0KiB/s,w=84.8MiB/s][r=0,w=21.7k IOPS][eta 00m:20sJobs: 1 (f=1): [w(1)][59.6%][r=0KiB/s,w=88.2MiB/s][r=0,w=22.6k IOPS][eta 00m:19sJobs: 1 (f=1): [w(1)][61.7%][r=0KiB/s,w=87.4MiB/s][r=0,w=22.4k IOPS][eta 00m:18sJobs: 1 (f=1): [w(1)][63.8%][r=0KiB/s,w=87.8MiB/s][r=0,w=22.5k IOPS][eta 00m:17sJobs: 1 (f=1): [w(1)][66.0%][r=0KiB/s,w=78.9MiB/s][r=0,w=20.2k IOPS][eta 00m:16sJobs: 1 (f=1): [w(1)][68.1%][r=0KiB/s,w=84.1MiB/s][r=0,w=21.5k IOPS][eta 00m:15sJobs: 1 (f=1): [w(1)][70.2%][r=0KiB/s,w=80.0MiB/s][r=0,w=20.7k IOPS][eta 00m:14sJobs: 1 (f=1): [w(1)][72.3%][r=0KiB/s,w=86.4MiB/s][r=0,w=22.1k IOPS][eta 00m:13sJobs: 1 (f=1): [w(1)][74.5%][r=0KiB/s,w=87.4MiB/s][r=0,w=22.4k IOPS][eta 00m:12sJobs: 1 (f=1): [w(1)][76.6%][r=0KiB/s,w=81.1MiB/s][r=0,w=20.8k IOPS][eta 00m:11sJobs: 1 (f=1): [w(1)][77.1%][r=0KiB/s,w=83.8MiB/s][r=0,w=21.5k IOPS][eta 00m:11sJobs: 1 (f=1): [w(1)][79.2%][r=0KiB/s,w=84.7MiB/s][r=0,w=21.7k IOPS][eta 00m:10sJobs: 1 (f=1): [w(1)][81.2%][r=0KiB/s,w=83.2MiB/s][r=0,w=21.3k IOPS][eta 00m:09sJobs: 1 (f=1): [w(1)][83.3%][r=0KiB/s,w=87.8MiB/s][r=0,w=22.5k IOPS][eta 00m:08sJobs: 1 (f=1): [w(1)][85.4%][r=0KiB/s,w=80.4MiB/s][r=0,w=20.6k IOPS][eta 00m:07sJobs: 1 (f=1): [w(1)][87.5%][r=0KiB/s,w=86.8MiB/s][r=0,w=22.2k IOPS][eta 00m:06sJobs: 1 (f=1): [w(1)][89.6%][r=0KiB/s,w=84.4MiB/s][r=0,w=21.6k IOPS][eta 00m:05sJobs: 1 (f=1): [w(1)][91.7%][r=0KiB/s,w=84.8MiB/s][r=0,w=21.7k IOPS][eta 00m:04sJobs: 1 (f=1): [w(1)][93.8%][r=0KiB/s,w=84.5MiB/s][r=0,w=21.6k IOPS][eta 00m:03sJobs: 1 (f=1): [w(1)][95.8%][r=0KiB/s,w=83.8MiB/s][r=0,w=21.5k IOPS][eta 00m:02sJobs: 1 (f=1): [w(1)][97.9%][r=0KiB/s,w=82.0MiB/s][r=0,w=21.0k IOPS][eta 00m:01sJobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=85.9MiB/s][r=0,w=21.0k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14987: Mon Nov 27 15:38:56 2017
  write: IOPS=21.8k, BW=85.3MiB/s (89.4MB/s)(4096MiB/48035msec)
    slat (usec): min=2, max=32939, avg= 8.88, stdev=79.25
    clat (usec): min=13, max=34831, avg=173.18, stdev=165.41
     lat (usec): min=55, max=34840, avg=182.26, stdev=184.40
    clat percentiles (usec):
     |  1.00th=[   58],  5.00th=[   65], 10.00th=[   75], 20.00th=[  124],
     | 30.00th=[  155], 40.00th=[  163], 50.00th=[  172], 60.00th=[  182],
     | 70.00th=[  196], 80.00th=[  212], 90.00th=[  243], 95.00th=[  277],
     | 99.00th=[  375], 99.50th=[  424], 99.90th=[  766], 99.95th=[ 1123],
     | 99.99th=[ 2638]
   bw (  KiB/s): min=76152, max=95632, per=100.00%, avg=87322.86, stdev=3802.92, samples=96
   iops        : min=19038, max=23908, avg=21830.70, stdev=950.75, samples=96
  lat (usec)   : 20=0.01%, 50=0.01%, 100=18.22%, 250=73.05%, 500=8.49%
  lat (usec)   : 750=0.13%, 1000=0.03%
  lat (msec)   : 2=0.06%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.01%
  cpu          : usr=3.06%, sys=22.59%, ctx=1048153, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=85.3MiB/s (89.4MB/s), 85.3MiB/s-85.3MiB/s (89.4MB/s-89.4MB/s), io=4096MiB (4295MB), run=48035-48035msec

Disk stats (read/write):
  sda: ios=0/1046084, merge=0/23160, ticks=0/182932, in_queue=182800, util=99.81%
```

*file-size*
```
ls -al test4Krandom-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 15:38 test4Krandom-aio
```

*reads*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=145MiB/s,w=0KiB/s][r=37.2k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14994: Mon Nov 27 15:40:03 2017
   read: IOPS=38.0k, BW=149MiB/s (156MB/s)(4096MiB/27573msec)
    slat (nsec): min=696, max=357456, avg=4141.56, stdev=3337.75
    clat (nsec): min=223, max=4513.4k, avg=100145.83, stdev=79553.37
     lat (nsec): min=1061, max=4516.0k, avg=104453.05, stdev=81073.65
    clat percentiles (nsec):
     |  1.00th=[    235],  5.00th=[    239], 10.00th=[    247],
     | 20.00th=[    310], 30.00th=[   5600], 40.00th=[ 132096],
     | 50.00th=[ 142336], 60.00th=[ 148480], 70.00th=[ 154624],
     | 80.00th=[ 160768], 90.00th=[ 171008], 95.00th=[ 183296],
     | 99.00th=[ 211968], 99.50th=[ 228352], 99.90th=[ 284672],
     | 99.95th=[ 436224], 99.99th=[1335296]
   bw (  KiB/s): min=138544, max=161568, per=99.99%, avg=152094.40, stdev=5223.26, samples=55
   iops        : min=34636, max=40392, avg=38023.60, stdev=1305.81, samples=55
  lat (nsec)   : 250=11.39%, 500=11.44%, 750=0.06%, 1000=0.01%
  lat (usec)   : 2=0.03%, 4=3.69%, 10=7.88%, 20=1.75%, 50=0.56%
  lat (usec)   : 100=0.01%, 250=62.97%, 500=0.17%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.02%, 4=0.01%, 10=0.01%
  cpu          : usr=3.61%, sys=21.08%, ctx=392440, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=149MiB/s (156MB/s), 149MiB/s-149MiB/s (156MB/s-156MB/s), io=4096MiB (4295MB), run=27573-27573msec

Disk stats (read/write):
  sda: ios=658402/3, merge=0/1, ticks=101164/0, in_queue=101100, util=99.38%
```

## itldc lax - 992M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            479M     0  479M   0% /dev
tmpfs           100M  3.0M   97M   3% /run
/dev/vda2       9.5G  1.7G  7.4G  19% /
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           497M     0  497M   0% /sys/fs/cgroup
```

*writes*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=4 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=210MiB/s][r=0,w=53.9k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2212: Mon Nov 27 06:38:34 2017
  write: IOPS=47.1k, BW=184MiB/s (193MB/s)(4096MiB/22279msec)
    slat (usec): min=2, max=5979, avg=13.44, stdev=13.78
    clat (nsec): min=610, max=17654k, avg=69287.70, stdev=62134.94
     lat (usec): min=18, max=17664, avg=83.16, stdev=64.88
    clat percentiles (usec):
     |  1.00th=[   25],  5.00th=[   34], 10.00th=[   39], 20.00th=[   46],
     | 30.00th=[   51], 40.00th=[   58], 50.00th=[   64], 60.00th=[   72],
     | 70.00th=[   79], 80.00th=[   87], 90.00th=[  100], 95.00th=[  117],
     | 99.00th=[  180], 99.50th=[  227], 99.90th=[  498], 99.95th=[  766],
     | 99.99th=[ 1909]
   bw (  KiB/s): min=160456, max=239320, per=99.90%, avg=188077.16, stdev=18042.84, samples=44
   iops        : min=40114, max=59830, avg=47019.27, stdev=4510.72, samples=44
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.22%, 50=27.88%, 100=62.06%, 250=9.44%
  lat (usec)   : 500=0.29%, 750=0.05%, 1000=0.02%
  lat (msec)   : 2=0.03%, 4=0.01%, 10=0.01%, 20=0.01%
  cpu          : usr=9.41%, sys=56.50%, ctx=556573, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=184MiB/s (193MB/s), 184MiB/s-184MiB/s (193MB/s-193MB/s), io=4096MiB (4295MB), run=22279-22279msec

Disk stats (read/write):
  vda: ios=0/1042118, merge=0/11218, ticks=0/53676, in_queue=54440, util=95.01%
```

*file-size*
```
ls -al test4Krandom-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 06:38 test4Krandom-aio
```

*reads*
```
./fio --filename=test4Krandom-aio --ioengine=libaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=4 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=505MiB/s,w=0KiB/s][r=129k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2218: Mon Nov 27 06:39:39 2017
   read: IOPS=132k, BW=515MiB/s (540MB/s)(4096MiB/7947msec)
    slat (nsec): min=961, max=279002, avg=3946.13, stdev=2452.83
    clat (nsec): min=289, max=1447.1k, avg=25282.01, stdev=19999.39
     lat (nsec): min=1458, max=1449.9k, avg=29456.35, stdev=21052.66
    clat percentiles (nsec):
     |  1.00th=[   322],  5.00th=[   330], 10.00th=[  3312], 20.00th=[  7904],
     | 30.00th=[ 13504], 40.00th=[ 21376], 50.00th=[ 25728], 60.00th=[ 29312],
     | 70.00th=[ 33024], 80.00th=[ 38144], 90.00th=[ 45824], 95.00th=[ 52992],
     | 99.00th=[ 73216], 99.50th=[ 85504], 99.90th=[150528], 99.95th=[211968],
     | 99.99th=[370688]
   bw (  KiB/s): min=476440, max=572760, per=99.57%, avg=525535.47, stdev=30063.22, samples=15
   iops        : min=119110, max=143190, avg=131383.87, stdev=7515.80, samples=15
  lat (nsec)   : 500=7.59%, 750=0.80%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=3.01%, 10=13.66%, 20=12.74%, 50=55.57%
  lat (usec)   : 100=6.33%, 250=0.26%, 500=0.03%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%
  cpu          : usr=13.14%, sys=65.24%, ctx=134968, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=515MiB/s (540MB/s), 515MiB/s-515MiB/s (540MB/s-540MB/s), io=4096MiB (4295MB), run=7947-7947msec

Disk stats (read/write):
  vda: ios=657980/3, merge=0/1, ticks=17152/8, in_queue=17100, util=88.99%
```

## impactvps ovz - 1024M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/simfs       15G  1.1G   14G   7% /
devtmpfs        512M     0  512M   0% /dev
tmpfs           512M     0  512M   0% /dev/shm
tmpfs           512M  6.7M  506M   2% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           512M     0  512M   0% /sys/fs/cgroup
tmpfs           103M     0  103M   0% /run/user/901
```

*writes*
```

```

*file-size*
```

```

*reads*
```

```
