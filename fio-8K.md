# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test8K --rw=write --ioengine=posixaio --direct=1 --blocksize=8K --size=4G --iodepth=32 --group_reporting --name=myjob

# random reads
fio --filename=test8K --rw=read --ioengine=posixaio --direct=1 --blocksize=8K --runtime=300 --iodepth=32 --group_reporting --name=myjob
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
./fio --filename=test8K --rw=write --ioengine=posixaio --direct=1 --blocksize=8K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 8192B-8192B, (W) 8192B-8192B, (T) 8192B-8192B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=53.8MiB/s][r=0,w=6880 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16190: Thu Oct  5 17:37:33 2017
  write: IOPS=6919, BW=54.1MiB/s (56.7MB/s)(4096MiB/75772msec)
    slat (nsec): min=220, max=68796, avg=526.89, stdev=279.00
    clat (usec): min=3200, max=91995, avg=4612.52, stdev=4451.04
     lat (usec): min=3200, max=91996, avg=4613.04, stdev=4451.05
    clat percentiles (usec):
     |  1.00th=[ 3556],  5.00th=[ 3720], 10.00th=[ 3785], 20.00th=[ 3884],
     | 30.00th=[ 3982], 40.00th=[ 4047], 50.00th=[ 4146], 60.00th=[ 4293],
     | 70.00th=[ 4490], 80.00th=[ 4686], 90.00th=[ 4883], 95.00th=[ 5276],
     | 99.00th=[ 8029], 99.50th=[18744], 99.90th=[83362], 99.95th=[85459],
     | 99.99th=[90702]
   bw (  KiB/s): min=35768, max=66560, per=100.00%, avg=55353.17, stdev=6927.33, samples=151
   iops        : min= 4471, max= 8320, avg=6919.15, stdev=865.92, samples=151
  lat (msec)   : 4=33.40%, 10=65.88%, 20=0.24%, 50=0.13%, 100=0.35%
  cpu          : usr=1.16%, sys=0.48%, ctx=262122, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,524288,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=54.1MiB/s (56.7MB/s), 54.1MiB/s-54.1MiB/s (56.7MB/s-56.7MB/s), io=4096MiB (4295MB), run=75772-75772msec

Disk stats (read/write):
  vda: ios=0/523604, merge=0/97, ticks=0/71192, in_queue=71140, util=92.73%
```

*file-size*
```
ls -al test8K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 17:37 test8K
```

*reads*
```
./fio --filename=test8K --rw=read --ioengine=posixaio --direct=1 --blocksize=8K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 8192B-8192B, (W) 8192B-8192B, (T) 8192B-8192B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][15.4%][r=98.3MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][17.9%][r=94.5MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][20.0%][r=91.0MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][23.1%][r=112MiB/s,w=0KiB/s][r=14.3k,w=0 IOPS][eta 00m:30s]Jobs: 1 (f=1): [R(1)][30.8%][r=93.6MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][32.5%][r=93.5MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][36.6%][r=94.5MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][37.5%][r=109MiB/s,w=0KiB/s][r=13.9k,w=0 IOPS][eta 00m:25s]Jobs: 1 (f=1): [R(1)][74.4%][r=95.8MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][76.3%][r=87.8MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][78.9%][r=87.7MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][82.1%][r=100MiB/s,w=0KiB/s][r=12.8k,w=0 IOPS][eta 00m:07s]Jobs: 1 (f=1): [R(1)][84.6%][r=85.5MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][87.2%][r=86.6MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [R(1)][89.7%][r=119MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:04s]Jobs: 1 (f=1): [R(1)][94.9%][r=97.8MiB/s,w=0KiB/s][r=12.5k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [R(1)][97.4%][r=98.7MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [R(1)][100.0%][r=85.8MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16195: Thu Oct  5 17:38:31 2017
   read: IOPS=13.3k, BW=104MiB/s (109MB/s)(4096MiB/39556msec)
    slat (nsec): min=176, max=68084, avg=261.03, stdev=173.65
    clat (usec): min=1667, max=12606, avg=2405.60, stdev=370.84
     lat (usec): min=1668, max=12606, avg=2405.86, stdev=370.85
    clat percentiles (usec):
     |  1.00th=[ 1778],  5.00th=[ 1876], 10.00th=[ 1958], 20.00th=[ 2089],
     | 30.00th=[ 2212], 40.00th=[ 2311], 50.00th=[ 2376], 60.00th=[ 2474],
     | 70.00th=[ 2540], 80.00th=[ 2704], 90.00th=[ 2835], 95.00th=[ 2966],
     | 99.00th=[ 3392], 99.50th=[ 3621], 99.90th=[ 4686], 99.95th=[ 5735],
     | 99.99th=[ 9110]
   bw (  KiB/s): min=85504, max=128512, per=100.00%, avg=106055.29, stdev=12087.38, samples=79
   iops        : min=10688, max=16064, avg=13256.91, stdev=1510.92, samples=79
  lat (msec)   : 2=12.93%, 4=86.82%, 10=0.24%, 20=0.01%
  cpu          : usr=1.47%, sys=0.98%, ctx=262158, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=524288,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=104MiB/s (109MB/s), 104MiB/s-104MiB/s (109MB/s-109MB/s), io=4096MiB (4295MB), run=39556-39556msec

Disk stats (read/write):
  vda: ios=522552/5, merge=0/1, ticks=35932/0, in_queue=35896, util=90.91%
```

