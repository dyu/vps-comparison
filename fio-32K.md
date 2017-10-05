# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test32K --rw=write --ioengine=posixaio --direct=1 --blocksize=32K --size=4G --iodepth=32 --group_reporting --name=myjob

# random reads
fio --filename=test32K --rw=read --ioengine=posixaio --direct=1 --blocksize=32K --runtime=300 --iodepth=32 --group_reporting --name=myjob
```

## aws ec2 micro - 990M
*writes*
```

```

*file-size*
```

```

*reads*
```

```

## gcloud micro - 585M
*writes*
```

```

*file-size*
```

```

*reads*
```

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

