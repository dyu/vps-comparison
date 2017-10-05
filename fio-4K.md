# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=32 --group_reporting --name=myjob

# random reads
fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=32 --group_reporting --name=myjob
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
./fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=31.6MiB/s][r=0,w=8099 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16204: Thu Oct  5 17:42:09 2017
  write: IOPS=6887, BW=26.9MiB/s (28.2MB/s)(4096MiB/152245msec)
    slat (nsec): min=194, max=81357, avg=423.32, stdev=250.39
    clat (msec): min=3, max=249, avg= 4.63, stdev= 4.67
     lat (msec): min=3, max=249, avg= 4.64, stdev= 4.67
    clat percentiles (msec):
     |  1.00th=[    4],  5.00th=[    4], 10.00th=[    4], 20.00th=[    4],
     | 30.00th=[    4], 40.00th=[    5], 50.00th=[    5], 60.00th=[    5],
     | 70.00th=[    5], 80.00th=[    5], 90.00th=[    6], 95.00th=[    6],
     | 99.00th=[    8], 99.50th=[   10], 99.90th=[  103], 99.95th=[  121],
     | 99.99th=[  125]
   bw (  KiB/s): min=14336, max=35824, per=100.00%, avg=27561.23, stdev=3748.98, samples=304
   iops        : min= 3584, max= 8956, avg=6890.31, stdev=937.25, samples=304
  lat (msec)   : 4=33.78%, 10=65.73%, 20=0.20%, 50=0.10%, 100=0.09%
  lat (msec)   : 250=0.11%
  cpu          : usr=1.06%, sys=0.50%, ctx=524330, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=26.9MiB/s (28.2MB/s), 26.9MiB/s-26.9MiB/s (28.2MB/s-28.2MB/s), io=4096MiB (4295MB), run=152245-152245msec

Disk stats (read/write):
  vda: ios=0/1048393, merge=0/157, ticks=0/143188, in_queue=143184, util=93.00%
```

*file-size*
```
ls -al test4K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 17:42 test4K
```

*reads*
```
./fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][10.6%][r=59.4MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 01m:16sJobs: 1 (f=1): [R(1)][12.0%][r=57.4MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 01m:13sJobs: 1 (f=1): [R(1)][13.3%][r=53.2MiB/s,w=0KiB/s][r=13.6k,w=0 IOPS][eta 01m:12sJobs: 1 (f=1): [R(1)][14.5%][r=49.3MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 01m:11sJobs: 1 (f=1): [R(1)][15.9%][r=57.1MiB/s,w=0KiB/s][r=14.6k,w=0 IOPS][eta 01m:09sJobs: 1 (f=1): [R(1)][17.3%][r=52.6MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 01m:07sJobs: 1 (f=1): [R(1)][18.5%][r=50.5MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 01m:06sJobs: 1 (f=1): [R(1)][19.8%][r=53.5MiB/s,w=0KiB/s][r=13.7k,w=0 IOPS][eta 01m:05sJobs: 1 (f=1): [R(1)][21.0%][r=52.8MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 01m:04sJobs: 1 (f=1): [R(1)][22.2%][r=48.1MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 01m:03sJobs: 1 (f=1): [R(1)][23.5%][r=54.0MiB/s,w=0KiB/s][r=13.8k,w=0 IOPS][eta 01m:02sJobs: 1 (f=1): [R(1)][25.0%][r=52.8MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 01m:00sJobs: 1 (f=1): [R(1)][26.2%][r=50.8MiB/s,w=0KiB/s][r=12.0k,w=0 IOPS][eta 00m:59sJobs: 1 (f=1): [R(1)][27.5%][r=54.9MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:58sJobs: 1 (f=1): [R(1)][28.7%][r=49.4MiB/s,w=0KiB/s][r=12.7k,w=0 IOPS][eta 00m:57sJobs: 1 (f=1): [R(1)][30.0%][r=55.2MiB/s,w=0KiB/s][r=14.1k,w=0 IOPS][eta 00m:56sJobs: 1 (f=1): [R(1)][31.2%][r=57.0MiB/s,w=0KiB/s][r=14.6k,w=0 IOPS][eta 00m:55sJobs: 1 (f=1): [R(1)][32.9%][r=59.1MiB/s,w=0KiB/s][r=15.1k,w=0 IOPS][eta 00m:53sJobs: 1 (f=1): [R(1)][34.2%][r=54.5MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [R(1)][35.4%][r=50.8MiB/s,w=0KiB/s][r=12.0k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [R(1)][37.2%][r=60.6MiB/s,w=0KiB/s][r=15.5k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [R(1)][38.5%][r=64.5MiB/s,w=0KiB/s][r=16.5k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [R(1)][40.3%][r=63.6MiB/s,w=0KiB/s][r=16.3k,w=0 IOPS][eta 00m:46sJobs: 1 (f=1): [R(1)][41.6%][r=65.6MiB/s,w=0KiB/s][r=16.8k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [R(1)][43.4%][r=65.9MiB/s,w=0KiB/s][r=16.9k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [R(1)][44.7%][r=57.4MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [R(1)][46.1%][r=52.5MiB/s,w=0KiB/s][r=13.4k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][47.4%][r=55.5MiB/s,w=0KiB/s][r=14.2k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [R(1)][48.7%][r=52.9MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [R(1)][50.0%][r=51.6MiB/s,w=0KiB/s][r=13.2k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [R(1)][51.3%][r=54.5MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [R(1)][52.6%][r=57.4MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][53.9%][r=56.8MiB/s,w=0KiB/s][r=14.5k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [R(1)][55.3%][r=54.6MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][56.6%][r=45.9MiB/s,w=0KiB/s][r=11.8k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][57.9%][r=53.4MiB/s,w=0KiB/s][r=13.7k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][59.2%][r=50.8MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][60.5%][r=57.5MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][61.8%][r=54.5MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][63.2%][r=55.4MiB/s,w=0KiB/s][r=14.2k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [R(1)][64.5%][r=64.2MiB/s,w=0KiB/s][r=16.4k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][65.8%][r=55.6MiB/s,w=0KiB/s][r=14.2k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][68.0%][r=56.1MiB/s,w=0KiB/s][r=14.4k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [R(1)][69.3%][r=58.1MiB/s,w=0KiB/s][r=14.9k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][70.7%][r=55.7MiB/s,w=0KiB/s][r=14.3k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][72.0%][r=59.2MiB/s,w=0KiB/s][r=15.1k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][73.3%][r=57.4MiB/s,w=0KiB/s][r=14.7k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [R(1)][74.7%][r=53.6MiB/s,w=0KiB/s][r=13.7k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [R(1)][76.0%][r=54.2MiB/s,w=0KiB/s][r=13.9k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][77.3%][r=58.0MiB/s,w=0KiB/s][r=14.8k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][78.7%][r=56.3MiB/s,w=0KiB/s][r=14.4k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [R(1)][80.0%][r=55.8MiB/s,w=0KiB/s][r=14.3k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [R(1)][81.3%][r=53.1MiB/s,w=0KiB/s][r=13.6k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][82.7%][r=60.3MiB/s,w=0KiB/s][r=15.4k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [R(1)][84.0%][r=66.5MiB/s,w=0KiB/s][r=17.0k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [R(1)][86.5%][r=59.1MiB/s,w=0KiB/s][r=15.1k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][87.8%][r=59.1MiB/s,w=0KiB/s][r=15.1k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][89.2%][r=59.9MiB/s,w=0KiB/s][r=15.3k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][90.5%][r=59.6MiB/s,w=0KiB/s][r=15.3k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [R(1)][91.9%][r=57.1MiB/s,w=0KiB/s][r=14.6k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][93.2%][r=54.4MiB/s,w=0KiB/s][r=13.9k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [R(1)][94.6%][r=54.9MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [R(1)][95.9%][r=59.3MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [R(1)][97.3%][r=51.0MiB/s,w=0KiB/s][r=13.1k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [R(1)][98.6%][r=50.8MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [R(1)][100.0%][r=56.6MiB/s,w=0KiB/s][r=14.5k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16209: Thu Oct  5 17:43:38 2017
   read: IOPS=14.1k, BW=54.9MiB/s (57.6MB/s)(4096MiB/74610msec)
    slat (nsec): min=174, max=72633, avg=260.24, stdev=158.11
    clat (usec): min=1561, max=17855, avg=2268.19, stdev=406.41
     lat (usec): min=1561, max=17856, avg=2268.45, stdev=406.41
    clat percentiles (usec):
     |  1.00th=[ 1696],  5.00th=[ 1795], 10.00th=[ 1860], 20.00th=[ 1991],
     | 30.00th=[ 2114], 40.00th=[ 2180], 50.00th=[ 2245], 60.00th=[ 2311],
     | 70.00th=[ 2376], 80.00th=[ 2474], 90.00th=[ 2638], 95.00th=[ 2802],
     | 99.00th=[ 3359], 99.50th=[ 3752], 99.90th=[ 6259], 99.95th=[ 8291],
     | 99.99th=[12518]
   bw (  KiB/s): min=42752, max=69120, per=100.00%, avg=56217.87, stdev=5519.06, samples=149
   iops        : min=10688, max=17280, avg=14054.46, stdev=1379.76, samples=149
  lat (msec)   : 2=20.36%, 4=79.26%, 10=0.34%, 20=0.03%
  cpu          : usr=1.79%, sys=0.83%, ctx=524325, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=54.9MiB/s (57.6MB/s), 54.9MiB/s-54.9MiB/s (57.6MB/s-57.6MB/s), io=4096MiB (4295MB), run=74610-74610msec

Disk stats (read/write):
  vda: ios=1045733/5, merge=0/1, ticks=67260/0, in_queue=67160, util=90.18%
```

