# fio results (all on ubuntu 16.04 x64)
```
# sequential writes
fio --filename=test32K --rw=write --ioengine=posixaio --direct=1 --blocksize=32K --size=4G --iodepth=32 --group_reporting --name=myjob

# sequential reads
fio --filename=test32K --rw=read --ioengine=posixaio --direct=1 --blocksize=32K --runtime=300 --iodepth=32 --group_reporting --name=myjob
```

## aws ec2 micro - 990M
*writes*
```
./fio --filename=test32K --rw=write --ioengine=posixaio --direct=1 --blocksize=32K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=31.2MiB/s][r=0,w=1000 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18815: Thu Oct  5 18:44:54 2017
  write: IOPS=991, BW=30.0MiB/s (32.5MB/s)(4096MiB/132228msec)
    slat (nsec): min=450, max=72039, avg=1741.99, stdev=552.99
    clat (msec): min=18, max=112, avg=32.25, stdev= 9.41
     lat (msec): min=18, max=112, avg=32.25, stdev= 9.41
    clat percentiles (msec):
     |  1.00th=[   24],  5.00th=[   24], 10.00th=[   25], 20.00th=[   25],
     | 30.00th=[   26], 40.00th=[   26], 50.00th=[   27], 60.00th=[   36],
     | 70.00th=[   37], 80.00th=[   40], 90.00th=[   48], 95.00th=[   51],
     | 99.00th=[   57], 99.50th=[   61], 99.90th=[   70], 99.95th=[   94],
     | 99.99th=[  112]
   bw (  KiB/s): min=22592, max=36864, per=99.99%, avg=31715.57, stdev=1994.42, samples=264
   iops        : min=  706, max= 1152, avg=991.07, stdev=62.30, samples=264
  lat (msec)   : 20=0.02%, 50=94.37%, 100=5.56%, 250=0.05%
  cpu          : usr=0.41%, sys=0.05%, ctx=65548, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,131072,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=30.0MiB/s (32.5MB/s), 30.0MiB/s-30.0MiB/s (32.5MB/s-32.5MB/s), io=4096MiB (4295MB), run=132228-132228msec

Disk stats (read/write):
  xvda: ios=0/131444, merge=0/85, ticks=0/131720, in_queue=131732, util=99.23%
```

*file-size*
```
ls -al test32K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:44 test32K
```

*reads*
```
./fio --filename=test32K --rw=read --ioengine=posixaio --direct=1 --blocksize=32K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=61.1MiB/s,w=0KiB/s][r=1953,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18822: Thu Oct  5 18:46:31 2017
   read: IOPS=1942, BW=60.7MiB/s (63.6MB/s)(4096MiB/67493msec)
    slat (nsec): min=183, max=68004, avg=368.61, stdev=341.94
    clat (msec): min=9, max=110, avg=16.46, stdev= 5.48
     lat (msec): min=9, max=110, avg=16.47, stdev= 5.48
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   11], 10.00th=[   11], 20.00th=[   12],
     | 30.00th=[   14], 40.00th=[   17], 50.00th=[   17], 60.00th=[   17],
     | 70.00th=[   17], 80.00th=[   21], 90.00th=[   24], 95.00th=[   25],
     | 99.00th=[   29], 99.50th=[   34], 99.90th=[   80], 99.95th=[   96],
     | 99.99th=[  101]
   bw (  KiB/s): min=34496, max=92416, per=99.99%, avg=62137.09, stdev=12334.78, samples=134
   iops        : min= 1078, max= 2888, avg=1941.77, stdev=385.48, samples=134
  lat (msec)   : 10=1.04%, 20=78.67%, 50=20.12%, 100=0.15%, 250=0.03%
  cpu          : usr=0.43%, sys=0.12%, ctx=65544, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=131072,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=60.7MiB/s (63.6MB/s), 60.7MiB/s-60.7MiB/s (63.6MB/s-63.6MB/s), io=4096MiB (4295MB), run=67493-67493msec

Disk stats (read/write):
  xvda: ios=131335/10, merge=0/2, ticks=66728/0, in_queue=66728, util=98.70%
```

## gcloud micro - 585M
*writes*
```
./fio --filename=test32K --rw=write --ioengine=posixaio --direct=1 --blocksize=32K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=29.2MiB/s][r=0,w=935 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=864: Thu Oct  5 18:46:32 2017
  write: IOPS=859, BW=26.9MiB/s (28.2MB/s)(4096MiB/152492msec)
    slat (nsec): min=406, max=708763, avg=2331.61, stdev=3777.48
    clat (msec): min=21, max=139, avg=37.19, stdev=10.52
     lat (msec): min=21, max=139, avg=37.19, stdev=10.52
    clat percentiles (msec):
     |  1.00th=[   24],  5.00th=[   26], 10.00th=[   27], 20.00th=[   29],
     | 30.00th=[   31], 40.00th=[   33], 50.00th=[   35], 60.00th=[   37],
     | 70.00th=[   41], 80.00th=[   45], 90.00th=[   52], 95.00th=[   58],
     | 99.00th=[   71], 99.50th=[   78], 99.90th=[   95], 99.95th=[  111],
     | 99.99th=[  140]
   bw (  KiB/s): min=11968, max=38720, per=100.00%, avg=27520.76, stdev=4925.83, samples=304
   iops        : min=  374, max= 1210, avg=860.01, stdev=153.93, samples=304
  lat (msec)   : 50=88.65%, 100=11.26%, 250=0.09%
  cpu          : usr=0.47%, sys=0.05%, ctx=65560, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,131072,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=26.9MiB/s (28.2MB/s), 26.9MiB/s-26.9MiB/s (28.2MB/s-28.2MB/s), io=4096MiB (4295MB), run=152492-152492msec

Disk stats (read/write):
  sda: ios=32/131104, merge=0/207, ticks=240/147148, in_queue=147324, util=96.47%
```

*file-size*
```
ls -al test32K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:46 test32K
```

*reads*
```
./fio --filename=test32K --rw=read --ioengine=posixaio --direct=1 --blocksize=32K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=62.1MiB/s,w=0KiB/s][r=1985,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=876: Thu Oct  5 18:48:06 2017
   read: IOPS=1884, BW=58.9MiB/s (61.7MB/s)(4096MiB/69556msec)
    slat (nsec): min=91, max=104526, avg=401.63, stdev=840.46
    clat (usec): min=2916, max=98784, avg=16966.50, stdev=14132.10
     lat (usec): min=2917, max=98785, avg=16966.90, stdev=14132.09
    clat percentiles (usec):
     |  1.00th=[ 3228],  5.00th=[ 3392], 10.00th=[ 3490], 20.00th=[ 3752],
     | 30.00th=[ 4948], 40.00th=[ 9634], 50.00th=[13698], 60.00th=[17695],
     | 70.00th=[22152], 80.00th=[27657], 90.00th=[36439], 95.00th=[44303],
     | 99.00th=[61080], 99.50th=[70779], 99.90th=[84411], 99.95th=[86508],
     | 99.99th=[99091]
   bw (  KiB/s): min=43008, max=77824, per=99.99%, avg=60293.76, stdev=7642.87, samples=139
   iops        : min= 1344, max= 2432, avg=1884.17, stdev=238.83, samples=139
  lat (msec)   : 4=25.45%, 10=15.32%, 20=24.41%, 50=32.02%, 100=2.81%
  cpu          : usr=0.50%, sys=0.13%, ctx=65548, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=131072,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=58.9MiB/s (61.7MB/s), 58.9MiB/s-58.9MiB/s (61.7MB/s-61.7MB/s), io=4096MiB (4295MB), run=69556-69556msec

Disk stats (read/write):
  sda: ios=130801/29, merge=0/13, ticks=66260/132, in_queue=66356, util=95.34%
```

## vultr - 488M
*writes*
```
./fio --filename=test32K --rw=write --ioengine=posixaio --direct=1 --blocksize=32K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=157MiB/s][r=0,w=5029 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11443: Thu Oct  5 18:14:20 2017
  write: IOPS=4414, BW=138MiB/s (145MB/s)(4096MiB/29691msec)
    slat (nsec): min=474, max=562931, avg=2678.32, stdev=2787.16
    clat (usec): min=5023, max=28181, avg=7203.24, stdev=1051.82
     lat (usec): min=5026, max=28185, avg=7205.92, stdev=1052.01
    clat percentiles (usec):
     |  1.00th=[ 5538],  5.00th=[ 5932], 10.00th=[ 6194], 20.00th=[ 6456],
     | 30.00th=[ 6652], 40.00th=[ 6849], 50.00th=[ 7046], 60.00th=[ 7242],
     | 70.00th=[ 7504], 80.00th=[ 7832], 90.00th=[ 8291], 95.00th=[ 8717],
     | 99.00th=[10683], 99.50th=[12256], 99.90th=[15795], 99.95th=[16909],
     | 99.99th=[23987]
   bw (  KiB/s): min=123136, max=166144, per=100.00%, avg=141287.15, stdev=10068.30, samples=59
   iops        : min= 3848, max= 5192, avg=4415.20, stdev=314.63, samples=59
  lat (msec)   : 10=98.54%, 20=1.42%, 50=0.05%
  cpu          : usr=2.53%, sys=0.81%, ctx=65526, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,131072,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=138MiB/s (145MB/s), 138MiB/s-138MiB/s (145MB/s-145MB/s), io=4096MiB (4295MB), run=29691-29691msec

Disk stats (read/write):
  vda: ios=0/130878, merge=0/193, ticks=0/25476, in_queue=25412, util=85.51%
```

*file-size*
```
ls -al test32K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:14 test32K
```

*reads*
```
./fio --filename=test32K --rw=read --ioengine=posixaio --direct=1 --blocksize=32K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=161MiB/s,w=0KiB/s][r=5164,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11450: Thu Oct  5 18:14:51 2017
   read: IOPS=5163, BW=161MiB/s (169MB/s)(4096MiB/25384msec)
    slat (nsec): min=206, max=190821, avg=701.53, stdev=1117.67
    clat (usec): min=4257, max=26903, avg=6173.15, stdev=1366.33
     lat (usec): min=4257, max=26904, avg=6173.85, stdev=1366.37
    clat percentiles (usec):
     |  1.00th=[ 4752],  5.00th=[ 5014], 10.00th=[ 5145], 20.00th=[ 5342],
     | 30.00th=[ 5538], 40.00th=[ 5669], 50.00th=[ 5866], 60.00th=[ 5997],
     | 70.00th=[ 6259], 80.00th=[ 6521], 90.00th=[ 7373], 95.00th=[ 8848],
     | 99.00th=[11600], 99.50th=[12911], 99.90th=[15401], 99.95th=[26346],
     | 99.99th=[26608]
   bw (  KiB/s): min=145408, max=184320, per=100.00%, avg=165371.40, stdev=8858.21, samples=50
   iops        : min= 4544, max= 5760, avg=5167.82, stdev=276.82, samples=50
  lat (msec)   : 10=97.42%, 20=2.51%, 50=0.07%
  cpu          : usr=1.89%, sys=0.77%, ctx=65560, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=131072,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=161MiB/s (169MB/s), 161MiB/s-161MiB/s (169MB/s-169MB/s), io=4096MiB (4295MB), run=25384-25384msec

Disk stats (read/write):
  vda: ios=129913/7, merge=0/17, ticks=22504/4, in_queue=22492, util=89.12%
```

## linode - 989M
*writes*
```
./fio --filename=test32K --rw=write --ioengine=posixaio --direct=1 --blocksize=32K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=215MiB/s][r=0,w=6880 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4882: Thu Oct  5 17:59:34 2017
  write: IOPS=8059, BW=252MiB/s (264MB/s)(4096MiB/16263msec)
    slat (nsec): min=504, max=167920, avg=1904.25, stdev=1111.63
    clat (usec): min=2620, max=17631, avg=3940.39, stdev=691.07
     lat (usec): min=2621, max=17633, avg=3942.29, stdev=691.23
    clat percentiles (usec):
     |  1.00th=[ 2900],  5.00th=[ 3097], 10.00th=[ 3228], 20.00th=[ 3458],
     | 30.00th=[ 3589], 40.00th=[ 3720], 50.00th=[ 3884], 60.00th=[ 4015],
     | 70.00th=[ 4178], 80.00th=[ 4359], 90.00th=[ 4686], 95.00th=[ 5014],
     | 99.00th=[ 5735], 99.50th=[ 6128], 99.90th=[ 9503], 99.95th=[15795],
     | 99.99th=[17695]
   bw (  KiB/s): min=206848, max=290816, per=99.88%, avg=257586.56, stdev=19917.11, samples=32
   iops        : min= 6464, max= 9088, avg=8049.56, stdev=622.45, samples=32
  lat (msec)   : 4=59.83%, 10=40.10%, 20=0.07%
  cpu          : usr=3.46%, sys=1.35%, ctx=65553, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,131072,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=252MiB/s (264MB/s), 252MiB/s-252MiB/s (264MB/s-264MB/s), io=4096MiB (4295MB), run=16263-16263msec

Disk stats (read/write):
  sda: ios=0/129333, merge=0/44, ticks=0/11250, in_queue=12447, util=66.73%
```

*file-size*
```
ls -al test32K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 17:59 test32K
```

*reads*
```
./fio --filename=test32K --rw=read --ioengine=posixaio --direct=1 --blocksize=32K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=276MiB/s,w=0KiB/s][r=8834,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4889: Thu Oct  5 18:00:01 2017
   read: IOPS=8493, BW=265MiB/s (278MB/s)(4096MiB/15432msec)
    slat (nsec): min=200, max=133366, avg=548.97, stdev=798.15
    clat (usec): min=2590, max=11171, avg=3752.32, stdev=574.39
     lat (usec): min=2591, max=11173, avg=3752.87, stdev=574.47
    clat percentiles (usec):
     |  1.00th=[ 2802],  5.00th=[ 2966], 10.00th=[ 3097], 20.00th=[ 3261],
     | 30.00th=[ 3425], 40.00th=[ 3556], 50.00th=[ 3687], 60.00th=[ 3851],
     | 70.00th=[ 4015], 80.00th=[ 4178], 90.00th=[ 4424], 95.00th=[ 4686],
     | 99.00th=[ 5342], 99.50th=[ 5866], 99.90th=[ 7373], 99.95th=[ 8848],
     | 99.99th=[11076]
   bw (  KiB/s): min=219575, max=310848, per=99.62%, avg=270760.23, stdev=23261.85, samples=30
   iops        : min= 6861, max= 9714, avg=8461.23, stdev=726.99, samples=30
  lat (msec)   : 4=69.61%, 10=30.35%, 20=0.05%
  cpu          : usr=2.46%, sys=1.16%, ctx=65548, majf=0, minf=21
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=131072,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=265MiB/s (278MB/s), 265MiB/s-265MiB/s (278MB/s-278MB/s), io=4096MiB (4295MB), run=15432-15432msec

Disk stats (read/write):
  sda: ios=130741/0, merge=0/0, ticks=10260/0, in_queue=10213, util=65.97%
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
*writes*
```
./fio --filename=test32K --rw=write --ioengine=posixaio --direct=1 --blocksize=32K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=161MiB/s][r=0,w=5157 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16163: Thu Oct  5 17:31:19 2017
  write: IOPS=4961, BW=155MiB/s (163MB/s)(4096MiB/26416msec)
    slat (nsec): min=362, max=80180, avg=1436.66, stdev=641.17
    clat (usec): min=4250, max=95703, avg=6426.19, stdev=6670.22
     lat (usec): min=4252, max=95705, avg=6427.62, stdev=6670.24
    clat percentiles (usec):
     |  1.00th=[ 4621],  5.00th=[ 4817], 10.00th=[ 4948], 20.00th=[ 5080],
     | 30.00th=[ 5145], 40.00th=[ 5276], 50.00th=[ 5342], 60.00th=[ 5538],
     | 70.00th=[ 5735], 80.00th=[ 6063], 90.00th=[ 6521], 95.00th=[ 7242],
     | 99.00th=[53740], 99.50th=[57934], 99.90th=[72877], 99.95th=[89654],
     | 99.99th=[95945]
   bw (  KiB/s): min=124608, max=186496, per=99.72%, avg=158335.83, stdev=16634.65, samples=52
   iops        : min= 3894, max= 5828, avg=4947.94, stdev=519.88, samples=52
  lat (msec)   : 10=97.68%, 20=0.66%, 50=0.29%, 100=1.37%
  cpu          : usr=1.36%, sys=0.35%, ctx=65547, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,131072,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=155MiB/s (163MB/s), 155MiB/s-155MiB/s (163MB/s-163MB/s), io=4096MiB (4295MB), run=26416-26416msec

Disk stats (read/write):
  vda: ios=0/130991, merge=0/109, ticks=0/24924, in_queue=24904, util=93.42%
```

*file-size*
```
ls -al test32K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 17:31 test32K
```

*reads*
```
./fio --filename=test32K --rw=read --ioengine=posixaio --direct=1 --blocksize=32K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 32.0KiB-32.0KiB, (W) 32.0KiB-32.0KiB, (T) 32.0KiB-32.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=319MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16169: Thu Oct  5 17:31:50 2017
   read: IOPS=9338, BW=292MiB/s (306MB/s)(4096MiB/14036msec)
    slat (nsec): min=175, max=60736, avg=281.00, stdev=279.24
    clat (usec): min=2346, max=8413, avg=3417.44, stdev=403.27
     lat (usec): min=2347, max=8414, avg=3417.73, stdev=403.28
    clat percentiles (usec):
     |  1.00th=[ 2507],  5.00th=[ 2868], 10.00th=[ 2999], 20.00th=[ 3130],
     | 30.00th=[ 3228], 40.00th=[ 3294], 50.00th=[ 3359], 60.00th=[ 3458],
     | 70.00th=[ 3589], 80.00th=[ 3720], 90.00th=[ 3851], 95.00th=[ 3982],
     | 99.00th=[ 4490], 99.50th=[ 4883], 99.90th=[ 6521], 99.95th=[ 7898],
     | 99.99th=[ 8455]
   bw (  KiB/s): min=258304, max=350208, per=100.00%, avg=298861.71, stdev=23431.83, samples=28
   iops        : min= 8072, max=10944, avg=9339.43, stdev=732.24, samples=28
  lat (msec)   : 4=95.10%, 10=4.90%
  cpu          : usr=1.08%, sys=0.71%, ctx=65542, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=131072,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=292MiB/s (306MB/s), 292MiB/s-292MiB/s (306MB/s-306MB/s), io=4096MiB (4295MB), run=14036-14036msec

Disk stats (read/write):
  vda: ios=129838/2, merge=0/1, ticks=12972/0, in_queue=12964, util=92.63%
```

