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

```

*file-size*
```

```

*reads*
```

```

## linode - 989M
*writes*
```

```

*file-size*
```

```

*reads*
```

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

