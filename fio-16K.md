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
./fio --filename=test16K --rw=write --ioengine=posixaio --direct=1 --blocksize=16K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 16.0KiB-16.0KiB, (W) 16.0KiB-16.0KiB, (T) 16.0KiB-16.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=92.0MiB/s][r=0,w=5888 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11511: Thu Oct  5 18:23:16 2017
  write: IOPS=5980, BW=93.4MiB/s (97.0MB/s)(4096MiB/43832msec)
    slat (nsec): min=339, max=1128.7k, avg=1519.35, stdev=3280.99
    clat (usec): min=3660, max=25559, avg=5318.66, stdev=876.90
     lat (usec): min=3661, max=25560, avg=5320.18, stdev=877.04
    clat percentiles (usec):
     |  1.00th=[ 4113],  5.00th=[ 4359], 10.00th=[ 4490], 20.00th=[ 4686],
     | 30.00th=[ 4883], 40.00th=[ 5014], 50.00th=[ 5211], 60.00th=[ 5342],
     | 70.00th=[ 5538], 80.00th=[ 5800], 90.00th=[ 6194], 95.00th=[ 6587],
     | 99.00th=[ 7963], 99.50th=[ 8979], 99.90th=[13173], 99.95th=[15139],
     | 99.99th=[25297]
   bw (  KiB/s): min=78909, max=114688, per=99.99%, avg=95683.14, stdev=7718.88, samples=87
   iops        : min= 4931, max= 7168, avg=5980.18, stdev=482.45, samples=87
  lat (msec)   : 4=0.37%, 10=99.30%, 20=0.30%, 50=0.03%
  cpu          : usr=2.58%, sys=0.97%, ctx=131105, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,262144,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=93.4MiB/s (97.0MB/s), 93.4MiB/s-93.4MiB/s (97.0MB/s-97.0MB/s), io=4096MiB (4295MB), run=43832-43832msec

Disk stats (read/write):
  vda: ios=0/260985, merge=0/124, ticks=0/36456, in_queue=36392, util=83.25%
```

*file-size*
```
ls -al test16K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:23 test16K
```

*reads*
```
./fio --filename=test16K --rw=read --ioengine=posixaio --direct=1 --blocksize=16K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 16.0KiB-16.0KiB, (W) 16.0KiB-16.0KiB, (T) 16.0KiB-16.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=108MiB/s,w=0KiB/s][r=6880,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11520: Thu Oct  5 18:25:07 2017
   read: IOPS=7049, BW=110MiB/s (116MB/s)(4096MiB/37185msec)
    slat (nsec): min=190, max=550847, avg=654.53, stdev=1417.55
    clat (usec): min=2826, max=24898, avg=4516.75, stdev=1104.78
     lat (usec): min=2826, max=24899, avg=4517.41, stdev=1104.84
    clat percentiles (usec):
     |  1.00th=[ 3195],  5.00th=[ 3490], 10.00th=[ 3654], 20.00th=[ 3851],
     | 30.00th=[ 4015], 40.00th=[ 4146], 50.00th=[ 4293], 60.00th=[ 4424],
     | 70.00th=[ 4621], 80.00th=[ 4883], 90.00th=[ 5407], 95.00th=[ 6325],
     | 99.00th=[ 9503], 99.50th=[10421], 99.90th=[12649], 99.95th=[15795],
     | 99.99th=[24773]
   bw (  KiB/s): min=98304, max=134336, per=99.98%, avg=112772.77, stdev=6921.55, samples=74
   iops        : min= 6144, max= 8396, avg=7048.28, stdev=432.61, samples=74
  lat (msec)   : 4=29.60%, 10=69.72%, 20=0.67%, 50=0.01%
  cpu          : usr=2.13%, sys=1.28%, ctx=131040, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=262144,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=110MiB/s (116MB/s), 110MiB/s-110MiB/s (116MB/s-116MB/s), io=4096MiB (4295MB), run=37185-37185msec

Disk stats (read/write):
  vda: ios=261854/4, merge=0/3, ticks=32660/0, in_queue=32620, util=87.63%
```

## linode - 989M
*writes*
```
./fio --filename=test16K --rw=write --ioengine=posixaio --direct=1 --blocksize=16K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 16.0KiB-16.0KiB, (W) 16.0KiB-16.0KiB, (T) 16.0KiB-16.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=156MiB/s][r=0,w=9982 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4898: Thu Oct  5 18:01:47 2017
  write: IOPS=9117, BW=142MiB/s (149MB/s)(4096MiB/28752msec)
    slat (nsec): min=342, max=175937, avg=1244.52, stdev=941.12
    clat (usec): min=2409, max=14624, avg=3487.56, stdev=659.85
     lat (usec): min=2410, max=14625, avg=3488.80, stdev=659.98
    clat percentiles (usec):
     |  1.00th=[ 2606],  5.00th=[ 2769], 10.00th=[ 2868], 20.00th=[ 2999],
     | 30.00th=[ 3097], 40.00th=[ 3228], 50.00th=[ 3392], 60.00th=[ 3523],
     | 70.00th=[ 3654], 80.00th=[ 3884], 90.00th=[ 4228], 95.00th=[ 4621],
     | 99.00th=[ 5538], 99.50th=[ 6194], 99.90th=[ 8160], 99.95th=[13566],
     | 99.99th=[14222]
   bw (  KiB/s): min=119808, max=166912, per=100.00%, avg=145871.16, stdev=11723.13, samples=57
   iops        : min= 7488, max=10432, avg=9116.95, stdev=732.70, samples=57
  lat (msec)   : 4=84.82%, 10=15.12%, 20=0.06%
  cpu          : usr=3.01%, sys=1.54%, ctx=131102, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,262144,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=142MiB/s (149MB/s), 142MiB/s-142MiB/s (149MB/s-149MB/s), io=4096MiB (4295MB), run=28752-28752msec

Disk stats (read/write):
  sda: ios=0/261167, merge=0/49, ticks=0/19737, in_queue=19620, util=62.62%
```

*file-size*
```
ls -al test16K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:01 test16K
```

*reads*
```
./fio --filename=test16K --rw=read --ioengine=posixaio --direct=1 --blocksize=16K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 16.0KiB-16.0KiB, (W) 16.0KiB-16.0KiB, (T) 16.0KiB-16.0KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=200MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4905: Thu Oct  5 18:02:21 2017
   read: IOPS=10.7k, BW=168MiB/s (176MB/s)(4096MiB/24417msec)
    slat (nsec): min=198, max=639567, avg=522.14, stdev=1404.51
    clat (usec): min=1930, max=8831, avg=2966.21, stdev=555.63
     lat (usec): min=1930, max=8833, avg=2966.73, stdev=555.73
    clat percentiles (usec):
     |  1.00th=[ 2024],  5.00th=[ 2114], 10.00th=[ 2245], 20.00th=[ 2474],
     | 30.00th=[ 2638], 40.00th=[ 2802], 50.00th=[ 2933], 60.00th=[ 3097],
     | 70.00th=[ 3228], 80.00th=[ 3425], 90.00th=[ 3687], 95.00th=[ 3916],
     | 99.00th=[ 4359], 99.50th=[ 4555], 99.90th=[ 5211], 99.95th=[ 6063],
     | 99.99th=[ 8717]
   bw (  KiB/s): min=139264, max=243712, per=99.80%, avg=171441.67, stdev=22759.45, samples=48
   iops        : min= 8704, max=15232, avg=10715.10, stdev=1422.47, samples=48
  lat (msec)   : 2=0.48%, 4=95.94%, 10=3.58%
  cpu          : usr=2.62%, sys=1.69%, ctx=131101, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=262144,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=168MiB/s (176MB/s), 168MiB/s-168MiB/s (176MB/s-176MB/s), io=4096MiB (4295MB), run=24417-24417msec

Disk stats (read/write):
  sda: ios=261924/0, merge=0/0, ticks=15360/0, in_queue=15273, util=62.39%
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

