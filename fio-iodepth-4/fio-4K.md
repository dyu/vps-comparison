# fio results (all on ubuntu 16.04 x64)
```
# sequential writes
fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob

# sequential reads
fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
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

*writes* - capped to 90-100 iops (estimated to take longer than 25mins)
```
./fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
^Cbs: 1 (f=1): [W(1)][37.2%][r=0KiB/s,w=396KiB/s][r=0,w=99 IOPS][eta 25m:16s]   
fio: terminating on signal 2

myjob: (groupid=0, jobs=1): err= 0: pid=21508: Fri Oct  6 05:45:29 2017
  write: IOPS=434, BW=1738KiB/s (1779kB/s)(1523MiB/897271msec)
    slat (nsec): min=243, max=71385, avg=716.23, stdev=387.50
    clat (usec): min=640, max=89978, avg=9205.30, stdev=14488.39
     lat (usec): min=711, max=89980, avg=9206.02, stdev=14488.60
    clat percentiles (usec):
     |  1.00th=[ 1811],  5.00th=[ 1876], 10.00th=[ 1909], 20.00th=[ 1958],
     | 30.00th=[ 1991], 40.00th=[ 2040], 50.00th=[ 2073], 60.00th=[ 2147],
     | 70.00th=[ 2278], 80.00th=[14353], 90.00th=[40109], 95.00th=[40109],
     | 99.00th=[49021], 99.50th=[51119], 99.90th=[54264], 99.95th=[58459],
     | 99.99th=[63701]
   bw (  KiB/s): min=  368, max= 7024, per=100.00%, avg=1737.68, stdev=2326.41, samples=1794
   iops        : min=   92, max= 1756, avg=434.36, stdev=581.63, samples=1794
  lat (usec)   : 750=0.01%
  lat (msec)   : 2=30.42%, 4=46.91%, 10=1.58%, 20=3.50%, 50=16.84%
  lat (msec)   : 100=0.75%
  cpu          : usr=0.24%, sys=0.09%, ctx=779596, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,389774,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=1738KiB/s (1779kB/s), 1738KiB/s-1738KiB/s (1779kB/s-1779kB/s), io=1523MiB (1597MB), run=897271-897271msec

Disk stats (read/write):
  xvda: ios=1/389858, merge=0/134, ticks=12/895268, in_queue=895272, util=99.80%
```

*file-size*
```
ls -al test4K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:45 test4K
```

*reads* - capped to 100 iops
```
./fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=400KiB/s,w=0KiB/s][r=100,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=21533: Fri Oct  6 05:52:00 2017
   read: IOPS=130, BW=522KiB/s (534kB/s)(153MiB/300032msec)
    slat (nsec): min=202, max=77956, avg=940.08, stdev=611.00
    clat (usec): min=510, max=109984, avg=30672.66, stdev=16494.63
     lat (usec): min=588, max=109984, avg=30673.60, stdev=16494.90
    clat percentiles (usec):
     |  1.00th=[  1434],  5.00th=[  1516], 10.00th=[  1582], 20.00th=[  1745],
     | 30.00th=[ 40109], 40.00th=[ 40109], 50.00th=[ 40109], 60.00th=[ 40109],
     | 70.00th=[ 40109], 80.00th=[ 40109], 90.00th=[ 40109], 95.00th=[ 40109],
     | 99.00th=[ 41681], 99.50th=[ 43254], 99.90th=[ 48497], 99.95th=[ 50594],
     | 99.99th=[100140]
   bw (  KiB/s): min=  344, max=10024, per=100.00%, avg=521.47, stdev=1048.88, samples=600
   iops        : min=   86, max= 2506, avg=130.32, stdev=262.22, samples=600
  lat (usec)   : 750=0.01%, 1000=0.01%
  lat (msec)   : 2=22.42%, 4=1.92%, 10=0.02%, 20=0.01%, 50=75.56%
  lat (msec)   : 100=0.07%, 250=0.01%
  cpu          : usr=0.10%, sys=0.03%, ctx=78248, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=39121,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=522KiB/s (534kB/s), 522KiB/s-522KiB/s (534kB/s-534kB/s), io=153MiB (160MB), run=300032-300032msec

Disk stats (read/write):
  xvda: ios=39107/16, merge=0/12, ticks=299684/424, in_queue=300116, util=99.98%
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
./fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=5448KiB/s][r=0,w=1362 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2712: Fri Oct  6 05:44:15 2017
  write: IOPS=1279, BW=5116KiB/s (5239kB/s)(4096MiB/819772msec)
    slat (nsec): min=153, max=783027, avg=1014.21, stdev=1334.02
    clat (usec): min=1866, max=27181, avg=3123.38, stdev=1209.10
     lat (usec): min=1867, max=27182, avg=3124.40, stdev=1209.12
    clat percentiles (usec):
     |  1.00th=[ 2147],  5.00th=[ 2245], 10.00th=[ 2311], 20.00th=[ 2409],
     | 30.00th=[ 2507], 40.00th=[ 2606], 50.00th=[ 2704], 60.00th=[ 2868],
     | 70.00th=[ 3130], 80.00th=[ 3523], 90.00th=[ 4293], 95.00th=[ 5407],
     | 99.00th=[ 8356], 99.50th=[ 9372], 99.90th=[12256], 99.95th=[13435],
     | 99.99th=[16909]
   bw (  KiB/s): min= 2424, max= 7124, per=100.00%, avg=5129.30, stdev=897.63, samples=1639
   iops        : min=  606, max= 1781, avg=1282.22, stdev=224.39, samples=1639
  lat (msec)   : 2=0.03%, 4=87.08%, 10=12.55%, 20=0.34%, 50=0.01%
  cpu          : usr=0.95%, sys=0.31%, ctx=2097466, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=5116KiB/s (5239kB/s), 5116KiB/s-5116KiB/s (5239kB/s-5239kB/s), io=4096MiB (4295MB), run=819772-819772msec

Disk stats (read/write):
  sda: ios=3/1049001, merge=0/533, ticks=12/775060, in_queue=774556, util=94.49%
```

*file-size*
```
ls -al test4K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:44 test4K
```

*reads*
```
./fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=5273KiB/s,w=0KiB/s][r=1318,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2753: Fri Oct  6 05:50:25 2017
   read: IOPS=1384, BW=5540KiB/s (5673kB/s)(1623MiB/300003msec)
    slat (nsec): min=101, max=183808, avg=826.56, stdev=702.58
    clat (usec): min=1408, max=107321, avg=2884.82, stdev=3978.78
     lat (usec): min=1409, max=107322, avg=2885.65, stdev=3978.78
    clat percentiles (usec):
     |  1.00th=[ 1598],  5.00th=[ 1680], 10.00th=[ 1745], 20.00th=[ 1827],
     | 30.00th=[ 1893], 40.00th=[ 1975], 50.00th=[ 2073], 60.00th=[ 2180],
     | 70.00th=[ 2376], 80.00th=[ 2704], 90.00th=[ 3523], 95.00th=[ 4686],
     | 99.00th=[25560], 99.50th=[32113], 99.90th=[46924], 99.95th=[54789],
     | 99.99th=[67634]
   bw (  KiB/s): min= 3016, max= 7960, per=100.00%, avg=5539.98, stdev=839.95, samples=600
   iops        : min=  754, max= 1990, avg=1384.98, stdev=209.99, samples=600
  lat (msec)   : 2=42.93%, 4=49.91%, 10=4.72%, 20=0.87%, 50=1.49%
  lat (msec)   : 100=0.07%, 250=0.01%
  cpu          : usr=0.96%, sys=0.27%, ctx=831052, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=415486,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=5540KiB/s (5673kB/s), 5540KiB/s-5540KiB/s (5673kB/s-5673kB/s), io=1623MiB (1702MB), run=300003-300003msec

Disk stats (read/write):
  sda: ios=415356/68, merge=0/42, ticks=286904/376, in_queue=287144, util=95.64%
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
./fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][69.7%][r=0KiB/s,w=40.1MiB/s][r=0,w=10.3k IOPS][eta 00m:37sJobs: 1 (f=1): [W(1)][71.1%][r=0KiB/s,w=36.6MiB/s][r=0,w=9377 IOPS][eta 00m:35s]Jobs: 1 (f=1): [W(1)][82.6%][r=0KiB/s,w=40.4MiB/s][r=0,w=10.3k IOPS][eta 00m:21sJobs: 1 (f=1): [W(1)][83.5%][r=0KiB/s,w=41.6MiB/s][r=0,w=10.6k IOPS][eta 00m:20sJobs: 1 (f=1): [W(1)][84.3%][r=0KiB/s,w=35.0MiB/s][r=0,w=9204 IOPS][eta 00m:19s]Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=33.4MiB/s][r=0,w=8546 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14410: Fri Oct  6 05:32:44 2017
  write: IOPS=8621, BW=33.7MiB/s (35.3MB/s)(4096MiB/121629msec)
    slat (nsec): min=303, max=268824, avg=834.20, stdev=1007.90
    clat (usec): min=245, max=23096, avg=461.04, stdev=210.61
     lat (usec): min=246, max=23096, avg=461.87, stdev=210.69
    clat percentiles (usec):
     |  1.00th=[  285],  5.00th=[  318], 10.00th=[  338], 20.00th=[  367],
     | 30.00th=[  392], 40.00th=[  408], 50.00th=[  424], 60.00th=[  449],
     | 70.00th=[  482], 80.00th=[  529], 90.00th=[  611], 95.00th=[  685],
     | 99.00th=[  938], 99.50th=[ 1156], 99.90th=[ 2409], 99.95th=[ 3916],
     | 99.99th=[ 8291]
   bw (  KiB/s): min=28776, max=43872, per=100.00%, avg=34490.46, stdev=2844.47, samples=243
   iops        : min= 7194, max=10968, avg=8622.61, stdev=711.11, samples=243
  lat (usec)   : 250=0.01%, 500=74.64%, 750=22.44%, 1000=2.13%
  lat (msec)   : 2=0.65%, 4=0.10%, 10=0.04%, 20=0.01%, 50=0.01%
  cpu          : usr=4.29%, sys=3.12%, ctx=2097325, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=33.7MiB/s (35.3MB/s), 33.7MiB/s-33.7MiB/s (35.3MB/s-35.3MB/s), io=4096MiB (4295MB), run=121629-121629msec

Disk stats (read/write):
  vda: ios=0/1046888, merge=0/147, ticks=0/91500, in_queue=91288, util=75.18%
```

*file-size*
```
ls -al test4K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:32 test4K
```

*reads*
```
./fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][11.5%][r=41.9MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 01m:40sJobs: 1 (f=1): [R(1)][12.4%][r=37.1MiB/s,w=0KiB/s][r=9488,w=0 IOPS][eta 01m:39s]Jobs: 1 (f=1): [R(1)][25.2%][r=40.8MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 01m:26sJobs: 1 (f=1): [R(1)][26.1%][r=38.1MiB/s,w=0KiB/s][r=9765,w=0 IOPS][eta 01m:25s]Jobs: 1 (f=1): [R(1)][28.7%][r=41.4MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 01m:22sJobs: 1 (f=1): [R(1)][29.8%][r=41.5MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 01m:20sJobs: 1 (f=1): [R(1)][30.7%][r=36.2MiB/s,w=0KiB/s][r=9273,w=0 IOPS][eta 01m:19s]Jobs: 1 (f=1): [R(1)][38.3%][r=39.3MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 01m:11sJobs: 1 (f=1): [R(1)][39.1%][r=36.2MiB/s,w=0KiB/s][r=9277,w=0 IOPS][eta 01m:10s]Jobs: 1 (f=1): [R(1)][40.4%][r=41.9MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 01m:08sJobs: 1 (f=1): [R(1)][41.2%][r=38.7MiB/s,w=0KiB/s][r=9912,w=0 IOPS][eta 01m:07s]Jobs: 1 (f=1): [R(1)][45.6%][r=39.8MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 01m:02sJobs: 1 (f=1): [R(1)][46.9%][r=40.4MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 01m:00sJobs: 1 (f=1): [R(1)][47.8%][r=36.0MiB/s,w=0KiB/s][r=9222,w=0 IOPS][eta 00m:59s]Jobs: 1 (f=1): [R(1)][48.7%][r=42.7MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:58sJobs: 1 (f=1): [R(1)][49.6%][r=42.3MiB/s,w=0KiB/s][r=10.8k,w=0 IOPS][eta 00m:57sJobs: 1 (f=1): [R(1)][50.4%][r=34.8MiB/s,w=0KiB/s][r=8905,w=0 IOPS][eta 00m:56s]Jobs: 1 (f=1): [R(1)][60.7%][r=40.5MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [R(1)][61.6%][r=41.6MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [R(1)][62.5%][r=37.0MiB/s,w=0KiB/s][r=9472,w=0 IOPS][eta 00m:42s]Jobs: 1 (f=1): [R(1)][67.9%][r=43.7MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][68.8%][r=36.2MiB/s,w=0KiB/s][r=9259,w=0 IOPS][eta 00m:35s]Jobs: 1 (f=1): [R(1)][69.6%][r=39.8MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][70.5%][r=41.9MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][72.1%][r=44.9MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][73.0%][r=39.6MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][73.9%][r=41.0MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][74.8%][r=37.5MiB/s,w=0KiB/s][r=9605,w=0 IOPS][eta 00m:28s]Jobs: 1 (f=1): [R(1)][75.7%][r=41.3MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][76.6%][r=37.9MiB/s,w=0KiB/s][r=9690,w=0 IOPS][eta 00m:26s]Jobs: 1 (f=1): [R(1)][82.0%][r=39.3MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [R(1)][82.9%][r=36.7MiB/s,w=0KiB/s][r=9384,w=0 IOPS][eta 00m:19s]Jobs: 1 (f=1): [R(1)][83.8%][r=42.8MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][84.7%][r=38.7MiB/s,w=0KiB/s][r=9910,w=0 IOPS][eta 00m:17s]Jobs: 1 (f=1): [R(1)][86.4%][r=39.4MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [R(1)][87.3%][r=38.9MiB/s,w=0KiB/s][r=9949,w=0 IOPS][eta 00m:14s]Jobs: 1 (f=1): [R(1)][100.0%][r=17.4MiB/s,w=0KiB/s][r=4463,w=0 IOPS][eta 00m:00sJobs: 1 (f=1): [R(1)][100.0%][r=13.8MiB/s,w=0KiB/s][r=3535,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14437: Fri Oct  6 05:37:04 2017
   read: IOPS=8839, BW=34.5MiB/s (36.2MB/s)(4096MiB/118622msec)
    slat (nsec): min=231, max=511368, avg=630.25, stdev=1084.70
    clat (usec): min=228, max=68538, avg=449.99, stdev=333.96
     lat (usec): min=229, max=68539, avg=450.62, stdev=334.04
    clat percentiles (usec):
     |  1.00th=[  251],  5.00th=[  277], 10.00th=[  297], 20.00th=[  322],
     | 30.00th=[  347], 40.00th=[  363], 50.00th=[  383], 60.00th=[  404],
     | 70.00th=[  441], 80.00th=[  494], 90.00th=[  635], 95.00th=[  881],
     | 99.00th=[ 1483], 99.50th=[ 1893], 99.90th=[ 3195], 99.95th=[ 4424],
     | 99.99th=[ 8586]
   bw (  KiB/s): min=10608, max=48520, per=100.00%, avg=35383.91, stdev=7401.68, samples=237
   iops        : min= 2652, max=12130, avg=8845.96, stdev=1850.42, samples=237
  lat (usec)   : 250=0.88%, 500=79.87%, 750=11.92%, 1000=4.16%
  lat (msec)   : 2=2.76%, 4=0.35%, 10=0.05%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%
  cpu          : usr=3.89%, sys=3.38%, ctx=2097313, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=34.5MiB/s (36.2MB/s), 34.5MiB/s-34.5MiB/s (36.2MB/s-36.2MB/s), io=4096MiB (4295MB), run=118622-118622msec

Disk stats (read/write):
  vda: ios=1047836/12, merge=0/6, ticks=95208/0, in_queue=95028, util=80.24%
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
./fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][10.1%][r=0KiB/s,w=40.0MiB/s][r=0,w=10.5k IOPS][eta 01m:29sJobs: 1 (f=1): [W(1)][11.1%][r=0KiB/s,w=40.4MiB/s][r=0,w=10.4k IOPS][eta 01m:28sJobs: 1 (f=1): [W(1)][12.1%][r=0KiB/s,w=42.3MiB/s][r=0,w=10.8k IOPS][eta 01m:27sJobs: 1 (f=1): [W(1)][12.9%][r=0KiB/s,w=32.0MiB/s][r=0,w=8198 IOPS][eta 01m:28s]Jobs: 1 (f=1): [W(1)][14.7%][r=0KiB/s,w=39.5MiB/s][r=0,w=10.1k IOPS][eta 01m:27sJobs: 1 (f=1): [W(1)][15.5%][r=0KiB/s,w=33.1MiB/s][r=0,w=8471 IOPS][eta 01m:27s]Jobs: 1 (f=1): [W(1)][17.9%][r=0KiB/s,w=41.1MiB/s][r=0,w=10.5k IOPS][eta 01m:27sJobs: 1 (f=1): [W(1)][18.9%][r=0KiB/s,w=39.3MiB/s][r=0,w=10.1k IOPS][eta 01m:26sJobs: 1 (f=1): [W(1)][19.8%][r=0KiB/s,w=37.9MiB/s][r=0,w=9715 IOPS][eta 01m:25s]Jobs: 1 (f=1): [W(1)][21.7%][r=0KiB/s,w=41.2MiB/s][r=0,w=10.5k IOPS][eta 01m:23sJobs: 1 (f=1): [W(1)][22.9%][r=0KiB/s,w=41.3MiB/s][r=0,w=10.6k IOPS][eta 01m:21sJobs: 1 (f=1): [W(1)][23.8%][r=0KiB/s,w=40.3MiB/s][r=0,w=10.3k IOPS][eta 01m:20sJobs: 1 (f=1): [W(1)][24.8%][r=0KiB/s,w=41.3MiB/s][r=0,w=10.6k IOPS][eta 01m:19sJobs: 1 (f=1): [W(1)][25.7%][r=0KiB/s,w=41.2MiB/s][r=0,w=10.5k IOPS][eta 01m:18sJobs: 1 (f=1): [W(1)][26.7%][r=0KiB/s,w=38.6MiB/s][r=0,w=9884 IOPS][eta 01m:17s]Jobs: 1 (f=1): [W(1)][27.9%][r=0KiB/s,w=40.4MiB/s][r=0,w=10.3k IOPS][eta 01m:15sJobs: 1 (f=1): [W(1)][28.8%][r=0KiB/s,w=42.5MiB/s][r=0,w=10.9k IOPS][eta 01m:14sJobs: 1 (f=1): [W(1)][29.8%][r=0KiB/s,w=40.4MiB/s][r=0,w=10.3k IOPS][eta 01m:13sJobs: 1 (f=1): [W(1)][30.8%][r=0KiB/s,w=38.6MiB/s][r=0,w=9885 IOPS][eta 01m:12s]Jobs: 1 (f=1): [W(1)][31.7%][r=0KiB/s,w=40.3MiB/s][r=0,w=10.3k IOPS][eta 01m:11sJobs: 1 (f=1): [W(1)][32.7%][r=0KiB/s,w=37.7MiB/s][r=0,w=9643 IOPS][eta 01m:10s]Jobs: 1 (f=1): [W(1)][33.7%][r=0KiB/s,w=40.1MiB/s][r=0,w=10.3k IOPS][eta 01m:09sJobs: 1 (f=1): [W(1)][34.6%][r=0KiB/s,w=35.4MiB/s][r=0,w=9063 IOPS][eta 01m:08s]Jobs: 1 (f=1): [W(1)][47.2%][r=0KiB/s,w=40.3MiB/s][r=0,w=10.3k IOPS][eta 00m:57sJobs: 1 (f=1): [W(1)][48.1%][r=0KiB/s,w=37.7MiB/s][r=0,w=9653 IOPS][eta 00m:56s]Jobs: 1 (f=1): [W(1)][67.9%][r=0KiB/s,w=39.3MiB/s][r=0,w=10.1k IOPS][eta 00m:36sJobs: 1 (f=1): [W(1)][68.8%][r=0KiB/s,w=37.5MiB/s][r=0,w=9612 IOPS][eta 00m:35s]Jobs: 1 (f=1): [W(1)][70.5%][r=0KiB/s,w=39.7MiB/s][r=0,w=10.2k IOPS][eta 00m:33sJobs: 1 (f=1): [W(1)][72.1%][r=0KiB/s,w=40.4MiB/s][r=0,w=10.3k IOPS][eta 00m:31sJobs: 1 (f=1): [W(1)][72.3%][r=0KiB/s,w=33.4MiB/s][r=0,w=8551 IOPS][eta 00m:31s]Jobs: 1 (f=1): [W(1)][87.8%][r=0KiB/s,w=39.7MiB/s][r=0,w=10.2k IOPS][eta 00m:14sJobs: 1 (f=1): [W(1)][88.7%][r=0KiB/s,w=32.2MiB/s][r=0,w=8255 IOPS][eta 00m:13s]Jobs: 1 (f=1): [W(1)][90.4%][r=0KiB/s,w=41.9MiB/s][r=0,w=10.7k IOPS][eta 00m:11sJobs: 1 (f=1): [W(1)][91.3%][r=0KiB/s,w=39.5MiB/s][r=0,w=10.1k IOPS][eta 00m:10sJobs: 1 (f=1): [W(1)][93.0%][r=0KiB/s,w=40.6MiB/s][r=0,w=10.4k IOPS][eta 00m:08sJobs: 1 (f=1): [W(1)][93.9%][r=0KiB/s,w=40.8MiB/s][r=0,w=10.5k IOPS][eta 00m:07sJobs: 1 (f=1): [W(1)][94.7%][r=0KiB/s,w=40.6MiB/s][r=0,w=10.4k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][95.7%][r=0KiB/s,w=42.4MiB/s][r=0,w=10.8k IOPS][eta 00m:05sJobs: 1 (f=1): [W(1)][96.5%][r=0KiB/s,w=42.8MiB/s][r=0,w=10.9k IOPS][eta 00m:04sJobs: 1 (f=1): [W(1)][97.4%][r=0KiB/s,w=41.2MiB/s][r=0,w=10.5k IOPS][eta 00m:03sJobs: 1 (f=1): [W(1)][99.1%][r=0KiB/s,w=41.6MiB/s][r=0,w=10.6k IOPS][eta 00m:01sJobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=39.3MiB/s][r=0,w=10.1k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14009: Fri Oct  6 05:32:40 2017
  write: IOPS=9230, BW=36.1MiB/s (37.8MB/s)(4096MiB/113602msec)
    slat (nsec): min=264, max=126898, avg=1006.09, stdev=596.41
    clat (usec): min=272, max=9101, avg=429.50, stdev=143.13
     lat (usec): min=272, max=9102, avg=430.51, stdev=143.24
    clat percentiles (usec):
     |  1.00th=[  306],  5.00th=[  322], 10.00th=[  330], 20.00th=[  351],
     | 30.00th=[  367], 40.00th=[  383], 50.00th=[  408], 60.00th=[  433],
     | 70.00th=[  461], 80.00th=[  502], 90.00th=[  553], 95.00th=[  594],
     | 99.00th=[  693], 99.50th=[  758], 99.90th=[ 1483], 99.95th=[ 2278],
     | 99.99th=[ 7570]
   bw (  KiB/s): min=24032, max=45832, per=100.00%, avg=36919.77, stdev=4859.68, samples=227
   iops        : min= 6008, max=11458, avg=9229.94, stdev=1214.92, samples=227
  lat (usec)   : 500=79.70%, 750=19.76%, 1000=0.33%
  lat (msec)   : 2=0.15%, 4=0.04%, 10=0.02%
  cpu          : usr=5.87%, sys=4.49%, ctx=2097429, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=36.1MiB/s (37.8MB/s), 36.1MiB/s-36.1MiB/s (37.8MB/s-37.8MB/s), io=4096MiB (4295MB), run=113602-113602msec

Disk stats (read/write):
  sda: ios=0/1046599, merge=0/112, ticks=0/61984, in_queue=61506, util=53.01%
```

*file-size*
```
ls -al test4K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:32 test4K
```

*reads*
```
./fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][10.1%][r=48.6MiB/s,w=0KiB/s][r=12.4k,w=0 IOPS][eta 01m:20sJobs: 1 (f=1): [R(1)][11.2%][r=47.4MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 01m:19sJobs: 1 (f=1): [R(1)][12.5%][r=47.0MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 01m:17sJobs: 1 (f=1): [R(1)][13.6%][r=47.4MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 01m:16sJobs: 1 (f=1): [R(1)][14.8%][r=49.4MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 01m:15sJobs: 1 (f=1): [R(1)][16.1%][r=50.7MiB/s,w=0KiB/s][r=12.0k,w=0 IOPS][eta 01m:13sJobs: 1 (f=1): [R(1)][17.2%][r=44.6MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 01m:12sJobs: 1 (f=1): [R(1)][18.4%][r=47.5MiB/s,w=0KiB/s][r=12.2k,w=0 IOPS][eta 01m:11sJobs: 1 (f=1): [R(1)][19.3%][r=44.1MiB/s,w=0KiB/s][r=11.3k,w=0 IOPS][eta 01m:11sJobs: 1 (f=1): [R(1)][20.5%][r=41.4MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 01m:10sJobs: 1 (f=1): [R(1)][21.3%][r=39.4MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 01m:10sJobs: 1 (f=1): [R(1)][23.3%][r=40.1MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 01m:09sJobs: 1 (f=1): [R(1)][23.3%][r=40.6MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 01m:09sJobs: 1 (f=1): [R(1)][25.3%][r=41.6MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 01m:08sJobs: 1 (f=1): [R(1)][25.3%][r=41.6MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 01m:08sJobs: 1 (f=1): [R(1)][27.2%][r=41.7MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 01m:07sJobs: 1 (f=1): [R(1)][27.5%][r=42.0MiB/s,w=0KiB/s][r=10.8k,w=0 IOPS][eta 01m:06sJobs: 1 (f=1): [R(1)][28.6%][r=47.6MiB/s,w=0KiB/s][r=12.2k,w=0 IOPS][eta 01m:05sJobs: 1 (f=1): [R(1)][29.7%][r=48.5MiB/s,w=0KiB/s][r=12.4k,w=0 IOPS][eta 01m:04sJobs: 1 (f=1): [R(1)][30.8%][r=43.0MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 01m:03sJobs: 1 (f=1): [R(1)][31.9%][r=42.6MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 01m:02sJobs: 1 (f=1): [R(1)][33.3%][r=51.9MiB/s,w=0KiB/s][r=13.3k,w=0 IOPS][eta 01m:00sJobs: 1 (f=1): [R(1)][34.1%][r=41.5MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 01m:00sJobs: 1 (f=1): [R(1)][35.9%][r=36.9MiB/s,w=0KiB/s][r=9438,w=0 IOPS][eta 00m:59s]Jobs: 1 (f=1): [R(1)][36.3%][r=46.4MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 00m:58sJobs: 1 (f=1): [R(1)][37.4%][r=50.6MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:57sJobs: 1 (f=1): [R(1)][38.9%][r=52.6MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 00m:55sJobs: 1 (f=1): [R(1)][40.0%][r=43.2MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:54sJobs: 1 (f=1): [R(1)][40.7%][r=38.0MiB/s,w=0KiB/s][r=9976,w=0 IOPS][eta 00m:54s]Jobs: 1 (f=1): [R(1)][42.4%][r=39.2MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 00m:53sJobs: 1 (f=1): [R(1)][42.9%][r=35.9MiB/s,w=0KiB/s][r=9196,w=0 IOPS][eta 00m:52s]Jobs: 1 (f=1): [R(1)][44.1%][r=39.7MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [R(1)][44.6%][r=43.2MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [R(1)][46.2%][r=47.1MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:50sJobs: 1 (f=1): [R(1)][46.7%][r=41.0MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [R(1)][48.4%][r=44.9MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [R(1)][48.9%][r=41.3MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [R(1)][50.5%][r=41.4MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 00m:46sJobs: 1 (f=1): [R(1)][51.6%][r=42.6MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [R(1)][52.2%][r=40.9MiB/s,w=0KiB/s][r=10.5k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [R(1)][53.8%][r=41.8MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [R(1)][53.8%][r=38.6MiB/s,w=0KiB/s][r=9884,w=0 IOPS][eta 00m:43s]Jobs: 1 (f=1): [R(1)][58.9%][r=39.4MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [R(1)][60.0%][r=37.4MiB/s,w=0KiB/s][r=9582,w=0 IOPS][eta 00m:38s]Jobs: 1 (f=1): [R(1)][63.5%][r=39.2MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [R(1)][64.2%][r=45.1MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][65.6%][r=41.1MiB/s,w=0KiB/s][r=10.5k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][66.3%][r=39.2MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][67.7%][r=43.1MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][68.4%][r=45.3MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][69.8%][r=39.8MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][70.5%][r=44.9MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [R(1)][71.9%][r=44.5MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][72.9%][r=43.3MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][74.0%][r=38.8MiB/s,w=0KiB/s][r=9933,w=0 IOPS][eta 00m:25s]Jobs: 1 (f=1): [R(1)][76.3%][r=40.3MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][77.3%][r=34.4MiB/s,w=0KiB/s][r=8809,w=0 IOPS][eta 00m:22s]Jobs: 1 (f=1): [R(1)][81.4%][r=39.5MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][82.5%][r=43.7MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][83.5%][r=42.6MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [R(1)][84.5%][r=47.9MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [R(1)][85.6%][r=42.3MiB/s,w=0KiB/s][r=10.8k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][86.6%][r=38.0MiB/s,w=0KiB/s][r=9735,w=0 IOPS][eta 00m:13s]Jobs: 1 (f=1): [R(1)][89.8%][r=40.4MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][90.8%][r=46.2MiB/s,w=0KiB/s][r=11.8k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][91.8%][r=45.5MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][92.9%][r=44.6MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [R(1)][93.9%][r=45.8MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][94.9%][r=46.7MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [R(1)][95.9%][r=46.2MiB/s,w=0KiB/s][r=11.8k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [R(1)][97.9%][r=45.3MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [R(1)][99.0%][r=46.9MiB/s,w=0KiB/s][r=12.0k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [R(1)][100.0%][r=48.7MiB/s,w=0KiB/s][r=12.5k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14019: Fri Oct  6 05:36:38 2017
   read: IOPS=10.9k, BW=42.4MiB/s (44.5MB/s)(4096MiB/96527msec)
    slat (nsec): min=270, max=142765, avg=872.94, stdev=520.71
    clat (usec): min=235, max=9095, avg=364.87, stdev=92.34
     lat (usec): min=235, max=9096, avg=365.74, stdev=92.45
    clat percentiles (usec):
     |  1.00th=[  265],  5.00th=[  277], 10.00th=[  289], 20.00th=[  302],
     | 30.00th=[  318], 40.00th=[  334], 50.00th=[  351], 60.00th=[  367],
     | 70.00th=[  388], 80.00th=[  416], 90.00th=[  457], 95.00th=[  498],
     | 99.00th=[  586], 99.50th=[  635], 99.90th=[  963], 99.95th=[ 1418],
     | 99.99th=[ 3490]
   bw (  KiB/s): min=28136, max=56328, per=100.00%, avg=43450.38, stdev=5101.42, samples=193
   iops        : min= 7034, max=14082, avg=10862.59, stdev=1275.36, samples=193
  lat (usec)   : 250=0.06%, 500=95.14%, 750=4.61%, 1000=0.10%
  lat (msec)   : 2=0.07%, 4=0.02%, 10=0.01%
  cpu          : usr=6.14%, sys=4.69%, ctx=2097362, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=42.4MiB/s (44.5MB/s), 42.4MiB/s-42.4MiB/s (44.5MB/s-44.5MB/s), io=4096MiB (4295MB), run=96527-96527msec

Disk stats (read/write):
  sda: ios=1046948/11, merge=0/8, ticks=52850/133, in_queue=52544, util=54.38%
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
./fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=22.9MiB/s][r=0,w=5856 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19074: Fri Oct  6 05:33:40 2017
  write: IOPS=6310, BW=24.7MiB/s (25.8MB/s)(4096MiB/166151msec)
    slat (nsec): min=209, max=69714, avg=494.82, stdev=238.50
    clat (usec): min=332, max=149991, avg=632.12, stdev=1624.95
     lat (usec): min=333, max=149991, avg=632.61, stdev=1624.95
    clat percentiles (usec):
     |  1.00th=[   449],  5.00th=[   482], 10.00th=[   498], 20.00th=[   523],
     | 30.00th=[   537], 40.00th=[   553], 50.00th=[   570], 60.00th=[   586],
     | 70.00th=[   603], 80.00th=[   619], 90.00th=[   668], 95.00th=[   750],
     | 99.00th=[  1237], 99.50th=[  2057], 99.90th=[  7111], 99.95th=[  9634],
     | 99.99th=[104334]
   bw (  KiB/s): min=14152, max=32168, per=100.00%, avg=25249.87, stdev=2961.80, samples=332
   iops        : min= 3538, max= 8042, avg=6312.46, stdev=740.46, samples=332
  lat (usec)   : 500=10.87%, 750=84.10%, 1000=3.32%
  lat (msec)   : 2=1.20%, 4=0.24%, 10=0.23%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%, 250=0.01%
  cpu          : usr=1.70%, sys=1.21%, ctx=2097234, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=24.7MiB/s (25.8MB/s), 24.7MiB/s-24.7MiB/s (25.8MB/s-25.8MB/s), io=4096MiB (4295MB), run=166151-166151msec

Disk stats (read/write):
  vda: ios=0/1048646, merge=0/134, ticks=0/151856, in_queue=151748, util=90.24%
```

*file-size*
```
ls -al test4K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:33 test4K
```

*reads*
```
./fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][10.5%][r=53.5MiB/s,w=0KiB/s][r=13.7k,w=0 IOPS][eta 01m:17sJobs: 1 (f=1): [R(1)][11.8%][r=50.9MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 01m:15sJobs: 1 (f=1): [R(1)][13.1%][r=51.1MiB/s,w=0KiB/s][r=13.1k,w=0 IOPS][eta 01m:13sJobs: 1 (f=1): [R(1)][14.3%][r=50.5MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 01m:12sJobs: 1 (f=1): [R(1)][15.5%][r=50.0MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 01m:11sJobs: 1 (f=1): [R(1)][16.7%][r=45.6MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 01m:10sJobs: 1 (f=1): [R(1)][17.6%][r=43.7MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 01m:10sJobs: 1 (f=1): [R(1)][18.8%][r=44.7MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 01m:09sJobs: 1 (f=1): [R(1)][20.0%][r=50.4MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 01m:08sJobs: 1 (f=1): [R(1)][21.2%][r=50.5MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 01m:07sJobs: 1 (f=1): [R(1)][22.4%][r=49.9MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 01m:06sJobs: 1 (f=1): [R(1)][23.5%][r=47.2MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 01m:05sJobs: 1 (f=1): [R(1)][24.7%][r=42.8MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 01m:04sJobs: 1 (f=1): [R(1)][25.9%][r=43.2MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 01m:03sJobs: 1 (f=1): [R(1)][27.1%][r=48.3MiB/s,w=0KiB/s][r=12.4k,w=0 IOPS][eta 01m:02sJobs: 1 (f=1): [R(1)][27.9%][r=44.3MiB/s,w=0KiB/s][r=11.3k,w=0 IOPS][eta 01m:02sJobs: 1 (f=1): [R(1)][29.1%][r=43.6MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 01m:01sJobs: 1 (f=1): [R(1)][30.2%][r=43.9MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 01m:00sJobs: 1 (f=1): [R(1)][31.4%][r=45.8MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:59sJobs: 1 (f=1): [R(1)][32.6%][r=50.3MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:58sJobs: 1 (f=1): [R(1)][33.7%][r=47.1MiB/s,w=0KiB/s][r=12.0k,w=0 IOPS][eta 00m:57sJobs: 1 (f=1): [R(1)][34.9%][r=43.8MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:56sJobs: 1 (f=1): [R(1)][35.6%][r=44.0MiB/s,w=0KiB/s][r=11.3k,w=0 IOPS][eta 00m:56sJobs: 1 (f=1): [R(1)][36.8%][r=45.6MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:55sJobs: 1 (f=1): [R(1)][38.4%][r=52.1MiB/s,w=0KiB/s][r=13.3k,w=0 IOPS][eta 00m:53sJobs: 1 (f=1): [R(1)][39.5%][r=46.9MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [R(1)][40.2%][r=43.4MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [R(1)][41.4%][r=43.5MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [R(1)][42.5%][r=45.5MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:50sJobs: 1 (f=1): [R(1)][43.7%][r=51.1MiB/s,w=0KiB/s][r=13.1k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [R(1)][44.8%][r=46.7MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [R(1)][46.0%][r=44.9MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [R(1)][47.1%][r=50.3MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:46sJobs: 1 (f=1): [R(1)][48.3%][r=42.7MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [R(1)][49.4%][r=45.0MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [R(1)][50.6%][r=44.3MiB/s,w=0KiB/s][r=11.3k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [R(1)][51.7%][r=43.4MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [R(1)][52.9%][r=46.5MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][54.0%][r=42.5MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [R(1)][55.2%][r=47.4MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [R(1)][56.3%][r=44.3MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [R(1)][57.5%][r=43.3MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [R(1)][58.6%][r=49.1MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][59.8%][r=51.9MiB/s,w=0KiB/s][r=13.3k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [R(1)][60.9%][r=49.1MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][62.1%][r=47.4MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][63.2%][r=45.3MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][64.4%][r=44.5MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][65.5%][r=44.7MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][66.7%][r=50.1MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][67.8%][r=44.9MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [R(1)][69.0%][r=42.8MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][70.1%][r=45.3MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][71.3%][r=43.9MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [R(1)][72.4%][r=49.4MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [R(1)][73.6%][r=45.2MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][74.7%][r=46.1MiB/s,w=0KiB/s][r=11.8k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][75.0%][r=39.8MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][76.1%][r=45.0MiB/s,w=0KiB/s][r=11.8k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][78.2%][r=52.2MiB/s,w=0KiB/s][r=13.4k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [R(1)][79.3%][r=49.7MiB/s,w=0KiB/s][r=12.7k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][80.5%][r=48.0MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][81.6%][r=42.6MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [R(1)][82.8%][r=47.0MiB/s,w=0KiB/s][r=12.0k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [R(1)][83.9%][r=50.0MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][85.1%][r=47.2MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [R(1)][86.2%][r=47.4MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [R(1)][87.4%][r=45.7MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [R(1)][88.5%][r=50.2MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][89.7%][r=52.1MiB/s,w=0KiB/s][r=13.3k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][90.8%][r=49.2MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][92.0%][r=49.2MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [R(1)][93.1%][r=45.5MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][94.3%][r=46.7MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [R(1)][95.4%][r=58.2MiB/s,w=0KiB/s][r=14.9k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [R(1)][96.6%][r=59.0MiB/s,w=0KiB/s][r=15.4k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [R(1)][98.8%][r=53.7MiB/s,w=0KiB/s][r=13.7k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [R(1)][100.0%][r=54.7MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19079: Fri Oct  6 05:36:23 2017
   read: IOPS=12.1k, BW=47.4MiB/s (49.7MB/s)(4096MiB/86440msec)
    slat (nsec): min=194, max=75272, avg=345.08, stdev=169.15
    clat (usec): min=183, max=11724, avg=328.54, stdev=82.17
     lat (usec): min=194, max=11724, avg=328.89, stdev=82.18
    clat percentiles (usec):
     |  1.00th=[  231],  5.00th=[  260], 10.00th=[  273], 20.00th=[  289],
     | 30.00th=[  302], 40.00th=[  314], 50.00th=[  322], 60.00th=[  334],
     | 70.00th=[  343], 80.00th=[  355], 90.00th=[  379], 95.00th=[  404],
     | 99.00th=[  545], 99.50th=[  644], 99.90th=[ 1057], 99.95th=[ 1401],
     | 99.99th=[ 2671]
   bw (  KiB/s): min=37384, max=62960, per=99.84%, avg=48444.09, stdev=4139.73, samples=172
   iops        : min= 9346, max=15740, avg=12111.02, stdev=1034.93, samples=172
  lat (usec)   : 250=2.82%, 500=95.69%, 750=1.22%, 1000=0.15%
  lat (msec)   : 2=0.09%, 4=0.02%, 10=0.01%, 20=0.01%
  cpu          : usr=2.30%, sys=2.06%, ctx=2097209, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=47.4MiB/s (49.7MB/s), 47.4MiB/s-47.4MiB/s (49.7MB/s-49.7MB/s), io=4096MiB (4295MB), run=86440-86440msec

Disk stats (read/write):
  vda: ios=1047958/4, merge=0/1, ticks=76504/0, in_queue=76404, util=88.36%
```

