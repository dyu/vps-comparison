# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test64K --rw=write --ioengine=posixaio --direct=1 --blocksize=64K --size=4G --iodepth=32 --group_reporting --name=myjob

# random reads
fio --filename=test64K --rw=read --ioengine=posixaio --direct=1 --blocksize=64K --runtime=300 --iodepth=32 --group_reporting --name=myjob
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

