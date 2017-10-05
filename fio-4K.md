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
./fio --filename=test4K --rw=write --ioengine=posixaio --direct=1 --blocksize=4K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][10.8%][r=0KiB/s,w=41.0MiB/s][r=0,w=10.8k IOPS][eta 01m:23sJobs: 1 (f=1): [W(1)][11.8%][r=0KiB/s,w=42.2MiB/s][r=0,w=10.8k IOPS][eta 01m:22sJobs: 1 (f=1): [W(1)][12.9%][r=0KiB/s,w=46.9MiB/s][r=0,w=12.0k IOPS][eta 01m:21sJobs: 1 (f=1): [W(1)][14.0%][r=0KiB/s,w=42.8MiB/s][r=0,w=10.0k IOPS][eta 01m:20sJobs: 1 (f=1): [W(1)][15.1%][r=0KiB/s,w=42.0MiB/s][r=0,w=10.8k IOPS][eta 01m:19sJobs: 1 (f=1): [W(1)][16.0%][r=0KiB/s,w=40.2MiB/s][r=0,w=10.3k IOPS][eta 01m:19sJobs: 1 (f=1): [W(1)][17.2%][r=0KiB/s,w=51.2MiB/s][r=0,w=13.1k IOPS][eta 01m:17sJobs: 1 (f=1): [W(1)][18.1%][r=0KiB/s,w=35.5MiB/s][r=0,w=9097 IOPS][eta 01m:17s]Jobs: 1 (f=1): [W(1)][19.1%][r=0KiB/s,w=42.5MiB/s][r=0,w=10.9k IOPS][eta 01m:16sJobs: 1 (f=1): [W(1)][20.4%][r=0KiB/s,w=47.0MiB/s][r=0,w=12.0k IOPS][eta 01m:14sJobs: 1 (f=1): [W(1)][21.7%][r=0KiB/s,w=54.9MiB/s][r=0,w=14.0k IOPS][eta 01m:12sJobs: 1 (f=1): [W(1)][23.1%][r=0KiB/s,w=50.7MiB/s][r=0,w=12.0k IOPS][eta 01m:10sJobs: 1 (f=1): [W(1)][23.9%][r=0KiB/s,w=38.2MiB/s][r=0,w=9792 IOPS][eta 01m:10s]Jobs: 1 (f=1): [W(1)][27.4%][r=0KiB/s,w=40.8MiB/s][r=0,w=10.4k IOPS][eta 01m:09sJobs: 1 (f=1): [W(1)][28.4%][r=0KiB/s,w=35.7MiB/s][r=0,w=9129 IOPS][eta 01m:08s]Jobs: 1 (f=1): [W(1)][34.0%][r=0KiB/s,w=40.6MiB/s][r=0,w=10.4k IOPS][eta 01m:06sJobs: 1 (f=1): [W(1)][35.0%][r=0KiB/s,w=46.0MiB/s][r=0,w=11.8k IOPS][eta 01m:05sJobs: 1 (f=1): [W(1)][36.4%][r=0KiB/s,w=47.3MiB/s][r=0,w=12.1k IOPS][eta 01m:03sJobs: 1 (f=1): [W(1)][37.4%][r=0KiB/s,w=38.3MiB/s][r=0,w=9798 IOPS][eta 01m:02s]Jobs: 1 (f=1): [W(1)][38.4%][r=0KiB/s,w=42.8MiB/s][r=0,w=10.9k IOPS][eta 01m:01sJobs: 1 (f=1): [W(1)][39.0%][r=0KiB/s,w=34.9MiB/s][r=0,w=8929 IOPS][eta 01m:01s]Jobs: 1 (f=1): [W(1)][41.0%][r=0KiB/s,w=39.7MiB/s][r=0,w=10.2k IOPS][eta 00m:59sJobs: 1 (f=1): [W(1)][42.0%][r=0KiB/s,w=36.9MiB/s][r=0,w=9441 IOPS][eta 00m:58s]Jobs: 1 (f=1): [W(1)][44.0%][r=0KiB/s,w=39.9MiB/s][r=0,w=10.2k IOPS][eta 00m:56sJobs: 1 (f=1): [W(1)][45.0%][r=0KiB/s,w=37.2MiB/s][r=0,w=9516 IOPS][eta 00m:55s]Jobs: 1 (f=1): [W(1)][48.5%][r=0KiB/s,w=40.7MiB/s][r=0,w=10.4k IOPS][eta 00m:52sJobs: 1 (f=1): [W(1)][49.5%][r=0KiB/s,w=39.6MiB/s][r=0,w=10.1k IOPS][eta 00m:51sJobs: 1 (f=1): [W(1)][50.5%][r=0KiB/s,w=41.4MiB/s][r=0,w=10.6k IOPS][eta 00m:50sJobs: 1 (f=1): [W(1)][51.5%][r=0KiB/s,w=45.0MiB/s][r=0,w=11.5k IOPS][eta 00m:49sJobs: 1 (f=1): [W(1)][52.5%][r=0KiB/s,w=38.5MiB/s][r=0,w=9864 IOPS][eta 00m:48s]Jobs: 1 (f=1): [W(1)][53.5%][r=0KiB/s,w=39.7MiB/s][r=0,w=10.2k IOPS][eta 00m:47sJobs: 1 (f=1): [W(1)][54.5%][r=0KiB/s,w=37.2MiB/s][r=0,w=9516 IOPS][eta 00m:46s]Jobs: 1 (f=1): [W(1)][56.4%][r=0KiB/s,w=41.4MiB/s][r=0,w=10.6k IOPS][eta 00m:44sJobs: 1 (f=1): [W(1)][57.4%][r=0KiB/s,w=37.8MiB/s][r=0,w=9664 IOPS][eta 00m:43s]Jobs: 1 (f=1): [W(1)][58.4%][r=0KiB/s,w=39.2MiB/s][r=0,w=10.0k IOPS][eta 00m:42sJobs: 1 (f=1): [W(1)][58.8%][r=0KiB/s,w=37.3MiB/s][r=0,w=9545 IOPS][eta 00m:42s]Jobs: 1 (f=1): [W(1)][60.8%][r=0KiB/s,w=44.7MiB/s][r=0,w=11.4k IOPS][eta 00m:40sJobs: 1 (f=1): [W(1)][61.8%][r=0KiB/s,w=38.2MiB/s][r=0,w=9792 IOPS][eta 00m:39s]Jobs: 1 (f=1): [W(1)][65.7%][r=0KiB/s,w=39.5MiB/s][r=0,w=10.1k IOPS][eta 00m:35sJobs: 1 (f=1): [W(1)][66.7%][r=0KiB/s,w=38.3MiB/s][r=0,w=9801 IOPS][eta 00m:34s]Jobs: 1 (f=1): [W(1)][70.6%][r=0KiB/s,w=39.9MiB/s][r=0,w=10.2k IOPS][eta 00m:30sJobs: 1 (f=1): [W(1)][71.6%][r=0KiB/s,w=36.4MiB/s][r=0,w=9315 IOPS][eta 00m:29s]Jobs: 1 (f=1): [W(1)][72.5%][r=0KiB/s,w=39.2MiB/s][r=0,w=10.0k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][73.5%][r=0KiB/s,w=41.4MiB/s][r=0,w=10.6k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][74.5%][r=0KiB/s,w=39.0MiB/s][r=0,w=9993 IOPS][eta 00m:26s]Jobs: 1 (f=1): [W(1)][75.5%][r=0KiB/s,w=42.1MiB/s][r=0,w=10.8k IOPS][eta 00m:25sJobs: 1 (f=1): [W(1)][76.5%][r=0KiB/s,w=40.8MiB/s][r=0,w=10.4k IOPS][eta 00m:24sJobs: 1 (f=1): [W(1)][77.5%][r=0KiB/s,w=37.9MiB/s][r=0,w=9698 IOPS][eta 00m:23s]Jobs: 1 (f=1): [W(1)][82.5%][r=0KiB/s,w=40.0MiB/s][r=0,w=10.2k IOPS][eta 00m:18sJobs: 1 (f=1): [W(1)][83.5%][r=0KiB/s,w=39.7MiB/s][r=0,w=10.2k IOPS][eta 00m:17sJobs: 1 (f=1): [W(1)][84.5%][r=0KiB/s,w=36.8MiB/s][r=0,w=9408 IOPS][eta 00m:16s]Jobs: 1 (f=1): [W(1)][85.4%][r=0KiB/s,w=40.7MiB/s][r=0,w=10.4k IOPS][eta 00m:15sJobs: 1 (f=1): [W(1)][86.4%][r=0KiB/s,w=34.6MiB/s][r=0,w=8863 IOPS][eta 00m:14s]Jobs: 1 (f=1): [W(1)][88.5%][r=0KiB/s,w=39.9MiB/s][r=0,w=10.2k IOPS][eta 00m:12sJobs: 1 (f=1): [W(1)][89.4%][r=0KiB/s,w=35.9MiB/s][r=0,w=9184 IOPS][eta 00m:11s]Jobs: 1 (f=1): [W(1)][94.2%][r=0KiB/s,w=39.5MiB/s][r=0,w=10.1k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][95.2%][r=0KiB/s,w=40.5MiB/s][r=0,w=10.4k IOPS][eta 00m:05sJobs: 1 (f=1): [W(1)][96.2%][r=0KiB/s,w=43.8MiB/s][r=0,w=11.2k IOPS][eta 00m:04sJobs: 1 (f=1): [W(1)][97.1%][r=0KiB/s,w=36.0MiB/s][r=0,w=9217 IOPS][eta 00m:03s]Jobs: 1 (f=1): [W(1)][99.0%][r=0KiB/s,w=40.2MiB/s][r=0,w=10.3k IOPS][eta 00m:01sJobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=40.1MiB/s][r=0,w=10.3k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4939: Thu Oct  5 18:08:50 2017
  write: IOPS=10.1k, BW=39.3MiB/s (41.2MB/s)(4096MiB/104229msec)
    slat (nsec): min=231, max=135238, avg=688.86, stdev=546.69
    clat (usec): min=2008, max=13959, avg=3164.43, stdev=609.82
     lat (usec): min=2009, max=13961, avg=3165.12, stdev=609.92
    clat percentiles (usec):
     |  1.00th=[ 2147],  5.00th=[ 2311], 10.00th=[ 2507], 20.00th=[ 2671],
     | 30.00th=[ 2835], 40.00th=[ 2966], 50.00th=[ 3097], 60.00th=[ 3228],
     | 70.00th=[ 3392], 80.00th=[ 3589], 90.00th=[ 3916], 95.00th=[ 4228],
     | 99.00th=[ 4752], 99.50th=[ 4948], 99.90th=[ 6456], 99.95th=[11469],
     | 99.99th=[12780]
   bw (  KiB/s): min=28616, max=57600, per=100.00%, avg=40244.68, stdev=5021.47, samples=208
   iops        : min= 7154, max=14400, avg=10061.16, stdev=1255.37, samples=208
  lat (msec)   : 4=91.76%, 10=8.17%, 20=0.06%
  cpu          : usr=2.89%, sys=1.45%, ctx=524386, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=39.3MiB/s (41.2MB/s), 39.3MiB/s-39.3MiB/s (41.2MB/s-41.2MB/s), io=4096MiB (4295MB), run=104229-104229msec

Disk stats (read/write):
  sda: ios=0/1047833, merge=0/134, ticks=0/64707, in_queue=64277, util=60.01%
```

*file-size*
```
ls -al test4K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:08 test4K
```

*reads*
```
./fio --filename=test4K --rw=read --ioengine=posixaio --direct=1 --blocksize=4K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][10.1%][r=39.8MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 01m:29sJobs: 1 (f=1): [R(1)][11.2%][r=43.0MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 01m:27sJobs: 1 (f=1): [R(1)][12.4%][r=46.5MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 01m:25sJobs: 1 (f=1): [R(1)][13.5%][r=48.4MiB/s,w=0KiB/s][r=12.4k,w=0 IOPS][eta 01m:23sJobs: 1 (f=1): [R(1)][14.6%][r=46.7MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 01m:22sJobs: 1 (f=1): [R(1)][15.6%][r=42.6MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 01m:21sJobs: 1 (f=1): [R(1)][16.8%][r=46.4MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 01m:19sJobs: 1 (f=1): [R(1)][18.1%][r=47.2MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 01m:17sJobs: 1 (f=1): [R(1)][19.1%][r=47.9MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 01m:16sJobs: 1 (f=1): [R(1)][20.2%][r=45.7MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 01m:15sJobs: 1 (f=1): [R(1)][21.5%][r=47.6MiB/s,w=0KiB/s][r=12.2k,w=0 IOPS][eta 01m:13sJobs: 1 (f=1): [R(1)][22.6%][r=44.8MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 01m:12sJobs: 1 (f=1): [R(1)][23.7%][r=45.8MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 01m:11sJobs: 1 (f=1): [R(1)][24.7%][r=41.7MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 01m:10sJobs: 1 (f=1): [R(1)][25.5%][r=39.3MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 01m:10sJobs: 1 (f=1): [R(1)][26.6%][r=43.2MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 01m:09sJobs: 1 (f=1): [R(1)][27.7%][r=43.3MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 01m:08sJobs: 1 (f=1): [R(1)][29.0%][r=44.8MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 01m:06sJobs: 1 (f=1): [R(1)][30.1%][r=43.8MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 01m:05sJobs: 1 (f=1): [R(1)][30.9%][r=41.9MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 01m:05sJobs: 1 (f=1): [R(1)][31.9%][r=43.4MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 01m:04sJobs: 1 (f=1): [R(1)][33.3%][r=46.5MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 01m:02sJobs: 1 (f=1): [R(1)][34.4%][r=44.2MiB/s,w=0KiB/s][r=11.3k,w=0 IOPS][eta 01m:01sJobs: 1 (f=1): [R(1)][35.1%][r=39.4MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 01m:01sJobs: 1 (f=1): [R(1)][36.2%][r=43.2MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 01m:00sJobs: 1 (f=1): [R(1)][37.6%][r=49.6MiB/s,w=0KiB/s][r=12.7k,w=0 IOPS][eta 00m:58sJobs: 1 (f=1): [R(1)][38.7%][r=43.7MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:57sJobs: 1 (f=1): [R(1)][39.8%][r=40.5MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 00m:56sJobs: 1 (f=1): [R(1)][41.1%][r=40.9MiB/s,w=0KiB/s][r=10.5k,w=0 IOPS][eta 00m:56sJobs: 1 (f=1): [R(1)][41.5%][r=45.7MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:55sJobs: 1 (f=1): [R(1)][43.6%][r=46.8MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:53sJobs: 1 (f=1): [R(1)][44.1%][r=44.2MiB/s,w=0KiB/s][r=11.3k,w=0 IOPS][eta 00m:52sJobs: 1 (f=1): [R(1)][45.7%][r=49.2MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [R(1)][46.2%][r=50.9MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:50sJobs: 1 (f=1): [R(1)][47.8%][r=50.3MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [R(1)][48.9%][r=49.8MiB/s,w=0KiB/s][r=12.7k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [R(1)][50.5%][r=45.5MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:46sJobs: 1 (f=1): [R(1)][51.1%][r=45.2MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [R(1)][52.7%][r=49.2MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [R(1)][53.3%][r=43.4MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [R(1)][54.8%][r=47.5MiB/s,w=0KiB/s][r=12.2k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [R(1)][55.4%][r=43.0MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][56.5%][r=46.7MiB/s,w=0KiB/s][r=11.9k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [R(1)][57.6%][r=43.1MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [R(1)][58.7%][r=47.9MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [R(1)][60.4%][r=52.1MiB/s,w=0KiB/s][r=13.3k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][61.5%][r=45.7MiB/s,w=0KiB/s][r=11.7k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [R(1)][62.6%][r=50.4MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][63.7%][r=52.6MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][65.6%][r=54.7MiB/s,w=0KiB/s][r=14.0k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][67.0%][r=45.0MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][67.8%][r=49.7MiB/s,w=0KiB/s][r=12.7k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][69.2%][r=49.1MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [R(1)][70.0%][r=51.2MiB/s,w=0KiB/s][r=13.1k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][71.4%][r=49.4MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][72.2%][r=41.4MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [R(1)][73.6%][r=50.6MiB/s,w=0KiB/s][r=12.0k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [R(1)][74.4%][r=48.7MiB/s,w=0KiB/s][r=12.5k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][75.8%][r=50.3MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][76.7%][r=44.9MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][78.0%][r=46.2MiB/s,w=0KiB/s][r=11.8k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [R(1)][78.9%][r=43.4MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [R(1)][80.0%][r=41.7MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][81.1%][r=46.8MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][82.4%][r=45.0MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [R(1)][83.3%][r=41.9MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [R(1)][84.6%][r=47.4MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][85.6%][r=41.2MiB/s,w=0KiB/s][r=10.5k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [R(1)][86.8%][r=39.2MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [R(1)][87.8%][r=39.5MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [R(1)][88.9%][r=42.6MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][90.0%][r=43.8MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][91.1%][r=40.3MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][92.2%][r=40.8MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [R(1)][92.3%][r=36.7MiB/s,w=0KiB/s][r=9385,w=0 IOPS][eta 00m:07s]Jobs: 1 (f=1): [R(1)][93.4%][r=43.0MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][94.5%][r=39.0MiB/s,w=0KiB/s][r=9993,w=0 IOPS][eta 00m:05s]Jobs: 1 (f=1): [R(1)][95.6%][r=41.4MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [R(1)][96.7%][r=41.4MiB/s,w=0KiB/s][r=10.6k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [R(1)][97.8%][r=40.1MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [R(1)][98.9%][r=42.2MiB/s,w=0KiB/s][r=10.8k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [R(1)][100.0%][r=41.0MiB/s,w=0KiB/s][r=10.7k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4946: Thu Oct  5 18:10:28 2017
   read: IOPS=11.4k, BW=44.7MiB/s (46.8MB/s)(4096MiB/91679msec)
    slat (nsec): min=196, max=171194, avg=502.38, stdev=510.47
    clat (usec): min=1774, max=18044, avg=2783.56, stdev=485.89
     lat (usec): min=1775, max=18045, avg=2784.06, stdev=485.98
    clat percentiles (usec):
     |  1.00th=[ 1991],  5.00th=[ 2147], 10.00th=[ 2245], 20.00th=[ 2376],
     | 30.00th=[ 2474], 40.00th=[ 2606], 50.00th=[ 2737], 60.00th=[ 2835],
     | 70.00th=[ 2999], 80.00th=[ 3163], 90.00th=[ 3392], 95.00th=[ 3621],
     | 99.00th=[ 4047], 99.50th=[ 4228], 99.90th=[ 4686], 99.95th=[ 5473],
     | 99.99th=[10552]
   bw (  KiB/s): min=35544, max=58680, per=100.00%, avg=45754.17, stdev=4448.01, samples=183
   iops        : min= 8886, max=14670, avg=11438.52, stdev=1112.00, samples=183
  lat (msec)   : 2=1.08%, 4=97.68%, 10=1.22%, 20=0.01%
  cpu          : usr=2.98%, sys=1.57%, ctx=524389, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=44.7MiB/s (46.8MB/s), 44.7MiB/s-44.7MiB/s (46.8MB/s-46.8MB/s), io=4096MiB (4295MB), run=91679-91679msec

Disk stats (read/write):
  sda: ios=1048151/9, merge=0/7, ticks=56633/67, in_queue=56320, util=61.37%
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

