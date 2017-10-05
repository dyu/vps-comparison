# fio results (all on ubuntu 16.04 x64)
```
# sequential writes
fio --filename=test64K --rw=write --ioengine=posixaio --direct=1 --blocksize=64K --size=4G --iodepth=32 --group_reporting --name=myjob

# sequential reads
fio --filename=test64K --rw=read --ioengine=posixaio --direct=1 --blocksize=64K --runtime=300 --iodepth=32 --group_reporting --name=myjob
```

## aws ec2 micro - 990M
*writes*
```
./fio --filename=test64K --rw=write --ioengine=posixaio --direct=1 --blocksize=64K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=48.3MiB/s][r=0,w=773 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18800: Thu Oct  5 18:39:42 2017
  write: IOPS=786, BW=49.2MiB/s (51.6MB/s)(4096MiB/83307msec)
    slat (nsec): min=862, max=69192, avg=3180.33, stdev=850.45
    clat (msec): min=28, max=154, avg=40.63, stdev=10.15
     lat (msec): min=28, max=154, avg=40.63, stdev=10.15
    clat percentiles (msec):
     |  1.00th=[   30],  5.00th=[   31], 10.00th=[   31], 20.00th=[   32],
     | 30.00th=[   32], 40.00th=[   33], 50.00th=[   42], 60.00th=[   44],
     | 70.00th=[   45], 80.00th=[   50], 90.00th=[   56], 95.00th=[   58],
     | 99.00th=[   64], 99.50th=[   68], 99.90th=[   78], 99.95th=[  104],
     | 99.99th=[  140]
   bw (  KiB/s): min=36790, max=57996, per=100.00%, avg=50354.99, stdev=3410.25, samples=166
   iops        : min=  574, max=  906, avg=786.77, stdev=53.30, samples=166
  lat (msec)   : 50=80.13%, 100=19.78%, 250=0.09%
  cpu          : usr=0.32%, sys=0.16%, ctx=32773, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,65536,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=49.2MiB/s (51.6MB/s), 49.2MiB/s-49.2MiB/s (51.6MB/s-51.6MB/s), io=4096MiB (4295MB), run=83307-83307msec

Disk stats (read/write):
  xvda: ios=0/65455, merge=0/83, ticks=0/82500, in_queue=82500, util=99.18%
```

*file-size*
```
ls -al test64K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:39 test64K
```

*reads*
```
./fio --filename=test64K --rw=read --ioengine=posixaio --direct=1 --blocksize=64K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=60.1MiB/s,w=0KiB/s][r=960,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18807: Thu Oct  5 18:40:58 2017
   read: IOPS=991, BW=61.0MiB/s (64.0MB/s)(4096MiB/66111msec)
    slat (nsec): min=183, max=63701, avg=401.54, stdev=465.14
    clat (usec): min=10954, max=77918, avg=32263.50, stdev=3683.88
     lat (usec): min=10954, max=77919, avg=32263.90, stdev=3683.88
    clat percentiles (usec):
     |  1.00th=[12911],  5.00th=[30802], 10.00th=[32637], 20.00th=[32637],
     | 30.00th=[32637], 40.00th=[32637], 50.00th=[32637], 60.00th=[32637],
     | 70.00th=[32900], 80.00th=[32900], 90.00th=[32900], 95.00th=[32900],
     | 99.00th=[36963], 99.50th=[40633], 99.90th=[62653], 99.95th=[73925],
     | 99.99th=[74974]
   bw (  KiB/s): min=57344, max=150656, per=99.95%, avg=63413.52, stdev=8451.59, samples=132
   iops        : min=  896, max= 2354, avg=990.80, stdev=132.05, samples=132
  lat (msec)   : 20=2.84%, 50=96.97%, 100=0.19%
  cpu          : usr=0.21%, sys=0.10%, ctx=32773, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=65536,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=61.0MiB/s (64.0MB/s), 61.0MiB/s-61.0MiB/s (64.0MB/s-64.0MB/s), io=4096MiB (4295MB), run=66111-66111msec

Disk stats (read/write):
  xvda: ios=65328/10, merge=0/10, ticks=65364/0, in_queue=65364, util=99.11%
```

## gcloud micro - 585M
*writes*
```
./fio --filename=test64K --rw=write --ioengine=posixaio --direct=1 --blocksize=64K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=24.0MiB/s][r=0,w=384 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=836: Thu Oct  5 18:40:57 2017
  write: IOPS=434, BW=27.2MiB/s (28.5MB/s)(4096MiB/150811msec)
    slat (nsec): min=816, max=600641, avg=3989.34, stdev=3199.60
    clat (msec): min=35, max=242, avg=73.57, stdev=23.45
     lat (msec): min=35, max=242, avg=73.58, stdev=23.45
    clat percentiles (msec):
     |  1.00th=[   40],  5.00th=[   46], 10.00th=[   50], 20.00th=[   55],
     | 30.00th=[   59], 40.00th=[   64], 50.00th=[   69], 60.00th=[   75],
     | 70.00th=[   82], 80.00th=[   90], 90.00th=[  105], 95.00th=[  118],
     | 99.00th=[  150], 99.50th=[  169], 99.90th=[  203], 99.95th=[  205],
     | 99.99th=[  215]
   bw (  KiB/s): min=12288, max=40960, per=100.00%, avg=27828.85, stdev=6380.11, samples=301
   iops        : min=  192, max=  640, avg=434.82, stdev=99.69, samples=301
  lat (msec)   : 50=11.59%, 100=75.86%, 250=12.55%
  cpu          : usr=0.31%, sys=0.03%, ctx=32787, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,65536,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=27.2MiB/s (28.5MB/s), 27.2MiB/s-27.2MiB/s (28.5MB/s-28.5MB/s), io=4096MiB (4295MB), run=150811-150811msec

Disk stats (read/write):
  sda: ios=0/65582, merge=0/168, ticks=0/147660, in_queue=147640, util=97.94%
```

*file-size*
```
ls -al test64K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:40 test64K
```

*reads*
```
./fio --filename=test64K --rw=read --ioengine=posixaio --direct=1 --blocksize=64K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=60.1MiB/s,w=0KiB/s][r=960,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=850: Thu Oct  5 18:42:13 2017
   read: IOPS=957, BW=59.9MiB/s (62.8MB/s)(4096MiB/68436msec)
    slat (nsec): min=95, max=90477, avg=441.58, stdev=895.14
    clat (msec): min=3, max=172, avg=33.40, stdev=15.88
     lat (msec): min=3, max=172, avg=33.40, stdev=15.88
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[   10], 10.00th=[   16], 20.00th=[   21],
     | 30.00th=[   26], 40.00th=[   29], 50.00th=[   32], 60.00th=[   36],
     | 70.00th=[   40], 80.00th=[   45], 90.00th=[   54], 95.00th=[   62],
     | 99.00th=[   84], 99.50th=[   89], 99.90th=[  107], 99.95th=[  117],
     | 99.99th=[  171]
   bw (  KiB/s): min=32768, max=77824, per=99.85%, avg=61196.20, stdev=7755.82, samples=136
   iops        : min=  512, max= 1216, avg=956.18, stdev=121.18, samples=136
  lat (msec)   : 4=0.08%, 10=5.40%, 20=12.85%, 50=69.09%, 100=12.27%
  lat (msec)   : 250=0.31%
  cpu          : usr=0.28%, sys=0.06%, ctx=32780, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=65536,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=59.9MiB/s (62.8MB/s), 59.9MiB/s-59.9MiB/s (62.8MB/s-62.8MB/s), io=4096MiB (4295MB), run=68436-68436msec

Disk stats (read/write):
  sda: ios=65441/18, merge=0/12, ticks=66692/172, in_queue=66832, util=97.37%
```

## vultr - 488M
*writes*
```
./fio --filename=test64K --rw=write --ioengine=posixaio --direct=1 --blocksize=64K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=180MiB/s][r=0,w=2878 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11427: Thu Oct  5 18:13:14 2017
  write: IOPS=2947, BW=184MiB/s (193MB/s)(4096MiB/22231msec)
    slat (nsec): min=1247, max=672066, avg=5393.02, stdev=5306.91
    clat (usec): min=7548, max=51232, avg=10775.95, stdev=1563.46
     lat (usec): min=7551, max=51237, avg=10781.34, stdev=1563.78
    clat percentiles (usec):
     |  1.00th=[ 8586],  5.00th=[ 9110], 10.00th=[ 9372], 20.00th=[ 9765],
     | 30.00th=[10159], 40.00th=[10421], 50.00th=[10552], 60.00th=[10814],
     | 70.00th=[11207], 80.00th=[11600], 90.00th=[12125], 95.00th=[12780],
     | 99.00th=[14353], 99.50th=[15795], 99.90th=[22938], 99.95th=[33817],
     | 99.99th=[50594]
   bw (  KiB/s): min=159744, max=217344, per=100.00%, avg=188695.27, stdev=12153.76, samples=44
   iops        : min= 2496, max= 3396, avg=2948.36, stdev=189.90, samples=44
  lat (msec)   : 10=25.85%, 20=73.96%, 50=0.14%, 100=0.05%
  cpu          : usr=2.66%, sys=0.68%, ctx=32789, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,65536,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=184MiB/s (193MB/s), 184MiB/s-184MiB/s (193MB/s-193MB/s), io=4096MiB (4295MB), run=22231-22231msec

Disk stats (read/write):
  vda: ios=0/65262, merge=0/87, ticks=0/19192, in_queue=19164, util=86.23%
```

*file-size*
```
ls -al test64K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:13 test64K
```

*reads*
```
./fio --filename=test64K --rw=read --ioengine=posixaio --direct=1 --blocksize=64K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=164MiB/s,w=0KiB/s][r=2626,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11434: Thu Oct  5 18:13:44 2017
   read: IOPS=3197, BW=200MiB/s (210MB/s)(4096MiB/20497msec)
    slat (nsec): min=228, max=196788, avg=863.23, stdev=2115.81
    clat (usec): min=6697, max=26976, avg=9977.03, stdev=2196.03
     lat (usec): min=6698, max=26978, avg=9977.89, stdev=2196.08
    clat percentiles (usec):
     |  1.00th=[ 7308],  5.00th=[ 7701], 10.00th=[ 8094], 20.00th=[ 8586],
     | 30.00th=[ 8848], 40.00th=[ 9110], 50.00th=[ 9372], 60.00th=[ 9765],
     | 70.00th=[10028], 80.00th=[10683], 90.00th=[12780], 95.00th=[14746],
     | 99.00th=[18220], 99.50th=[19268], 99.90th=[22414], 99.95th=[23462],
     | 99.99th=[26870]
   bw (  KiB/s): min=163840, max=253568, per=100.00%, avg=205822.50, stdev=15321.25, samples=40
   iops        : min= 2560, max= 3962, avg=3215.95, stdev=239.39, samples=40
  lat (msec)   : 10=68.38%, 20=31.23%, 50=0.38%
  cpu          : usr=1.44%, sys=0.66%, ctx=32774, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=65536,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=200MiB/s (210MB/s), 200MiB/s-200MiB/s (210MB/s-210MB/s), io=4096MiB (4295MB), run=20497-20497msec

Disk stats (read/write):
  vda: ios=65294/12, merge=0/3, ticks=18248/0, in_queue=18220, util=88.93%
```

## linode - 989M
*writes*
```
./fio --filename=test64K --rw=write --ioengine=posixaio --direct=1 --blocksize=64K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=374MiB/s][r=0,w=5984 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4865: Thu Oct  5 17:57:28 2017
  write: IOPS=6430, BW=402MiB/s (421MB/s)(4096MiB/10191msec)
    slat (nsec): min=814, max=285109, avg=3406.67, stdev=2102.18
    clat (usec): min=3283, max=21586, avg=4929.19, stdev=937.91
     lat (usec): min=3285, max=21590, avg=4932.60, stdev=938.26
    clat percentiles (usec):
     |  1.00th=[ 3589],  5.00th=[ 3916], 10.00th=[ 4080], 20.00th=[ 4293],
     | 30.00th=[ 4424], 40.00th=[ 4555], 50.00th=[ 4752], 60.00th=[ 4948],
     | 70.00th=[ 5211], 80.00th=[ 5538], 90.00th=[ 5997], 95.00th=[ 6456],
     | 99.00th=[ 7177], 99.50th=[ 7898], 99.90th=[10552], 99.95th=[20317],
     | 99.99th=[21627]
   bw (  KiB/s): min=339968, max=462976, per=99.87%, avg=411033.60, stdev=34508.83, samples=20
   iops        : min= 5312, max= 7234, avg=6422.40, stdev=539.20, samples=20
  lat (msec)   : 4=7.71%, 10=92.10%, 20=0.10%, 50=0.09%
  cpu          : usr=4.05%, sys=0.84%, ctx=32782, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,65536,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=402MiB/s (421MB/s), 402MiB/s-402MiB/s (421MB/s-421MB/s), io=4096MiB (4295MB), run=10191-10191msec

Disk stats (read/write):
  sda: ios=0/65163, merge=0/42, ticks=0/8354, in_queue=8566, util=71.72%
```

*file-size*
```
ls -al test64K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 17:57 test64K
```

*reads*
```
./fio --filename=test64K --rw=read --ioengine=posixaio --direct=1 --blocksize=64K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=641MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4872: Thu Oct  5 17:57:46 2017
   read: IOPS=9031, BW=564MiB/s (592MB/s)(4096MiB/7256msec)
    slat (nsec): min=198, max=137411, avg=498.09, stdev=801.21
    clat (usec): min=2508, max=10292, avg=3528.86, stdev=567.67
     lat (usec): min=2509, max=10293, avg=3529.36, stdev=567.73
    clat percentiles (usec):
     |  1.00th=[ 2671],  5.00th=[ 2802], 10.00th=[ 2900], 20.00th=[ 3097],
     | 30.00th=[ 3228], 40.00th=[ 3359], 50.00th=[ 3458], 60.00th=[ 3589],
     | 70.00th=[ 3720], 80.00th=[ 3884], 90.00th=[ 4146], 95.00th=[ 4424],
     | 99.00th=[ 5211], 99.50th=[ 6194], 99.90th=[ 8160], 99.95th=[ 8586],
     | 99.99th=[10290]
   bw (  KiB/s): min=524160, max=654464, per=100.00%, avg=579858.29, stdev=39485.42, samples=14
   iops        : min= 8190, max=10226, avg=9060.29, stdev=616.96, samples=14
  lat (msec)   : 4=84.21%, 10=15.74%, 20=0.05%
  cpu          : usr=2.38%, sys=1.09%, ctx=32778, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=65536,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=564MiB/s (592MB/s), 564MiB/s-564MiB/s (592MB/s-592MB/s), io=4096MiB (4295MB), run=7256-7256msec

Disk stats (read/write):
  sda: ios=64637/2, merge=0/6, ticks=4810/53, in_queue=4857, util=66.76%
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
*writes*
```
./fio --filename=test64K --rw=write --ioengine=posixaio --direct=1 --blocksize=64K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=230MiB/s][r=0,w=3686 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16152: Thu Oct  5 17:24:45 2017
  write: IOPS=3590, BW=224MiB/s (235MB/s)(4096MiB/18252msec)
    slat (nsec): min=598, max=62378, avg=2983.90, stdev=937.51
    clat (usec): min=5921, max=82100, avg=8870.80, stdev=8983.78
     lat (usec): min=5923, max=82103, avg=8873.79, stdev=8983.78
    clat percentiles (usec):
     |  1.00th=[ 6194],  5.00th=[ 6456], 10.00th=[ 6587], 20.00th=[ 6718],
     | 30.00th=[ 6849], 40.00th=[ 6980], 50.00th=[ 7111], 60.00th=[ 7242],
     | 70.00th=[ 7504], 80.00th=[ 7832], 90.00th=[ 8225], 95.00th=[ 9241],
     | 99.00th=[61080], 99.50th=[66323], 99.90th=[74974], 99.95th=[76022],
     | 99.99th=[82314]
   bw (  KiB/s): min=192512, max=258560, per=100.00%, avg=229890.36, stdev=18620.41, samples=36
   iops        : min= 3008, max= 4040, avg=3592.03, stdev=290.94, samples=36
  lat (msec)   : 10=95.86%, 20=0.77%, 50=0.78%, 100=2.59%
  cpu          : usr=1.58%, sys=0.26%, ctx=32779, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,65536,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=224MiB/s (235MB/s), 224MiB/s-224MiB/s (235MB/s-235MB/s), io=4096MiB (4295MB), run=18252-18252msec

Disk stats (read/write):
  vda: ios=0/65123, merge=0/74, ticks=0/17224, in_queue=17220, util=94.08%
```

*file-size*
```
ls -al test64K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 17:24 test64K
```

*reads*
```
./fio --filename=test64K --rw=read --ioengine=posixaio --direct=1 --blocksize=64K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=398MiB/s,w=0KiB/s][r=6375,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16157: Thu Oct  5 17:25:11 2017
   read: IOPS=6296, BW=394MiB/s (413MB/s)(4096MiB/10409msec)
    slat (nsec): min=176, max=60614, avg=299.73, stdev=312.86
    clat (usec): min=3239, max=30684, avg=5071.55, stdev=2425.81
     lat (usec): min=3239, max=30684, avg=5071.84, stdev=2425.81
    clat percentiles (usec):
     |  1.00th=[ 3523],  5.00th=[ 3720], 10.00th=[ 3916], 20.00th=[ 4228],
     | 30.00th=[ 4490], 40.00th=[ 4621], 50.00th=[ 4752], 60.00th=[ 4883],
     | 70.00th=[ 5014], 80.00th=[ 5145], 90.00th=[ 5407], 95.00th=[ 6063],
     | 99.00th=[18744], 99.50th=[24249], 99.90th=[30278], 99.95th=[30278],
     | 99.99th=[30540]
   bw (  KiB/s): min=360448, max=409600, per=99.92%, avg=402636.80, stdev=12008.71, samples=20
   iops        : min= 5632, max= 6400, avg=6291.20, stdev=187.64, samples=20
  lat (msec)   : 4=11.71%, 10=85.75%, 20=1.61%, 50=0.93%
  cpu          : usr=0.96%, sys=0.38%, ctx=32774, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=65536,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=394MiB/s (413MB/s), 394MiB/s-394MiB/s (413MB/s-413MB/s), io=4096MiB (4295MB), run=10409-10409msec

Disk stats (read/write):
  vda: ios=65481/2, merge=0/1, ticks=9680/0, in_queue=9680, util=92.23%
```

