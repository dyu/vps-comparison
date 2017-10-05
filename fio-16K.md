# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test16K --rw=write --ioengine=posixaio --direct=1 --blocksize=16K --size=4G --iodepth=32 --group_reporting --name=myjob

# random reads
fio --filename=test16K --rw=read --ioengine=posixaio --direct=1 --blocksize=16K --runtime=300 --iodepth=32 --group_reporting --name=myjob
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
./fio --filename=test16K --rw=write --ioengine=posixaio --direct=1 --blocksize=16K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 16.0KiB-16.0KiB, (W) 16.0KiB-16.0KiB, (T) 16.0KiB-16.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=91.0MiB/s][r=0,w=5827 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16177: Thu Oct  5 17:33:56 2017
  write: IOPS=6272, BW=98.0MiB/s (103MB/s)(4096MiB/41791msec)
    slat (nsec): min=260, max=59550, avg=778.16, stdev=376.92
    clat (usec): min=3538, max=80473, avg=5086.56, stdev=4919.93
     lat (usec): min=3538, max=80475, avg=5087.34, stdev=4919.93
    clat percentiles (usec):
     |  1.00th=[ 3916],  5.00th=[ 4080], 10.00th=[ 4178], 20.00th=[ 4228],
     | 30.00th=[ 4293], 40.00th=[ 4424], 50.00th=[ 4490], 60.00th=[ 4621],
     | 70.00th=[ 4817], 80.00th=[ 5014], 90.00th=[ 5276], 95.00th=[ 5538],
     | 99.00th=[ 9896], 99.50th=[56886], 99.90th=[68682], 99.95th=[69731],
     | 99.99th=[80217]
   bw (  KiB/s): min=75776, max=118784, per=100.00%, avg=100372.88, stdev=9215.39, samples=83
   iops        : min= 4736, max= 7424, avg=6273.29, stdev=575.97, samples=83
  lat (msec)   : 4=2.22%, 10=96.81%, 20=0.11%, 50=0.18%, 100=0.67%
  cpu          : usr=1.21%, sys=0.42%, ctx=131037, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,262144,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=98.0MiB/s (103MB/s), 98.0MiB/s-98.0MiB/s (103MB/s-103MB/s), io=4096MiB (4295MB), run=41791-41791msec

Disk stats (read/write):
  vda: ios=0/261537, merge=0/84, ticks=0/39360, in_queue=39352, util=93.25%
```

*file-size*
```
ls -al test16K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 17:33 test16K
```

*reads*
```
./fio --filename=test16K --rw=read --ioengine=posixaio --direct=1 --blocksize=16K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 16.0KiB-16.0KiB, (W) 16.0KiB-16.0KiB, (T) 16.0KiB-16.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=193MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16182: Thu Oct  5 17:34:41 2017
   read: IOPS=11.5k, BW=179MiB/s (188MB/s)(4096MiB/22836msec)
    slat (nsec): min=175, max=59604, avg=263.81, stdev=198.98
    clat (usec): min=1892, max=9369, avg=2778.65, stdev=321.54
     lat (usec): min=1892, max=9370, avg=2778.91, stdev=321.54
    clat percentiles (usec):
     |  1.00th=[ 2180],  5.00th=[ 2376], 10.00th=[ 2442], 20.00th=[ 2540],
     | 30.00th=[ 2638], 40.00th=[ 2704], 50.00th=[ 2737], 60.00th=[ 2802],
     | 70.00th=[ 2868], 80.00th=[ 2999], 90.00th=[ 3097], 95.00th=[ 3228],
     | 99.00th=[ 3785], 99.50th=[ 4178], 99.90th=[ 5211], 99.95th=[ 6325],
     | 99.99th=[ 8979]
   bw (  KiB/s): min=161792, max=222048, per=99.98%, avg=183628.42, stdev=12817.94, samples=45
   iops        : min=10112, max=13878, avg=11476.76, stdev=801.09, samples=45
  lat (msec)   : 2=0.20%, 4=99.13%, 10=0.66%
  cpu          : usr=1.17%, sys=0.96%, ctx=131084, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=262144,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=179MiB/s (188MB/s), 179MiB/s-179MiB/s (188MB/s-188MB/s), io=4096MiB (4295MB), run=22836-22836msec

Disk stats (read/write):
  vda: ios=259997/5, merge=0/1, ticks=20984/0, in_queue=20968, util=92.20%
```

