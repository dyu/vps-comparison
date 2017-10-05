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
./fio --filename=test8K --rw=write --ioengine=posixaio --direct=1 --blocksize=8K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 8192B-8192B, (W) 8192B-8192B, (T) 8192B-8192B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=57.8MiB/s][r=0,w=7399 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11546: Thu Oct  5 18:27:38 2017
  write: IOPS=7840, BW=61.3MiB/s (64.2MB/s)(4096MiB/66868msec)
    slat (nsec): min=256, max=3941.9k, avg=984.51, stdev=5573.62
    clat (usec): min=2355, max=17946, avg=4057.27, stdev=808.02
     lat (usec): min=2356, max=17947, avg=4058.26, stdev=808.18
    clat percentiles (usec):
     |  1.00th=[ 2868],  5.00th=[ 3130], 10.00th=[ 3326], 20.00th=[ 3523],
     | 30.00th=[ 3654], 40.00th=[ 3785], 50.00th=[ 3916], 60.00th=[ 4047],
     | 70.00th=[ 4228], 80.00th=[ 4490], 90.00th=[ 4883], 95.00th=[ 5342],
     | 99.00th=[ 6718], 99.50th=[ 7832], 99.90th=[11731], 99.95th=[13042],
     | 99.99th=[17695]
   bw (  KiB/s): min=52224, max=74704, per=100.00%, avg=62753.41, stdev=4658.95, samples=133
   iops        : min= 6528, max= 9338, avg=7844.17, stdev=582.38, samples=133
  lat (msec)   : 4=55.78%, 10=44.02%, 20=0.20%
  cpu          : usr=2.84%, sys=0.99%, ctx=262195, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,524288,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=61.3MiB/s (64.2MB/s), 61.3MiB/s-61.3MiB/s (64.2MB/s-64.2MB/s), io=4096MiB (4295MB), run=66868-66868msec

Disk stats (read/write):
  vda: ios=0/522781, merge=0/148, ticks=0/54712, in_queue=54524, util=81.74%
```

*file-size*
```
ls -al test8K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:27 test8K
```

*reads*
```
./fio --filename=test8K --rw=read --ioengine=posixaio --direct=1 --blocksize=8K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 8192B-8192B, (W) 8192B-8192B, (T) 8192B-8192B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][28.8%][r=78.5MiB/s,w=0KiB/s][r=10.1k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [R(1)][31.0%][r=72.3MiB/s,w=0KiB/s][r=9253,w=0 IOPS][eta 00m:40s]Jobs: 1 (f=1): [R(1)][43.9%][r=81.0MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][45.6%][r=69.8MiB/s,w=0KiB/s][r=8936,w=0 IOPS][eta 00m:31s]Jobs: 1 (f=1): [R(1)][70.2%][r=79.3MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][71.9%][r=76.5MiB/s,w=0KiB/s][r=9793,w=0 IOPS][eta 00m:16s]Jobs: 1 (f=1): [R(1)][100.0%][r=69.3MiB/s,w=0KiB/s][r=8867,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11560: Thu Oct  5 18:28:55 2017
   read: IOPS=9179, BW=71.7MiB/s (75.2MB/s)(4096MiB/57113msec)
    slat (nsec): min=183, max=1923.6k, avg=564.00, stdev=2818.45
    clat (usec): min=2130, max=24816, avg=3467.54, stdev=923.18
     lat (usec): min=2130, max=24818, avg=3468.10, stdev=923.25
    clat percentiles (usec):
     |  1.00th=[ 2474],  5.00th=[ 2671], 10.00th=[ 2802], 20.00th=[ 2966],
     | 30.00th=[ 3064], 40.00th=[ 3130], 50.00th=[ 3228], 60.00th=[ 3359],
     | 70.00th=[ 3523], 80.00th=[ 3752], 90.00th=[ 4228], 95.00th=[ 4948],
     | 99.00th=[ 7635], 99.50th=[ 8455], 99.90th=[10683], 99.95th=[11469],
     | 99.99th=[19530]
   bw (  KiB/s): min=46160, max=88160, per=99.97%, avg=73418.16, stdev=6219.23, samples=114
   iops        : min= 5770, max=11020, avg=9177.25, stdev=777.40, samples=114
  lat (msec)   : 4=86.74%, 10=13.07%, 20=0.18%, 50=0.01%
  cpu          : usr=2.47%, sys=1.25%, ctx=262199, majf=0, minf=18
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=524288,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=71.7MiB/s (75.2MB/s), 71.7MiB/s-71.7MiB/s (75.2MB/s-75.2MB/s), io=4096MiB (4295MB), run=57113-57113msec

Disk stats (read/write):
  vda: ios=522043/13, merge=0/3, ticks=48688/0, in_queue=48604, util=85.32%
```

## linode - 989M
*writes*
```
./fio --filename=test8K --rw=write --ioengine=posixaio --direct=1 --blocksize=8K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 8192B-8192B, (W) 8192B-8192B, (T) 8192B-8192B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][10.9%][r=0KiB/s,w=81.1MiB/s][r=0,w=10.4k IOPS][eta 00m:41sJobs: 1 (f=1): [W(1)][13.3%][r=0KiB/s,w=98.2MiB/s][r=0,w=12.6k IOPS][eta 00m:39sJobs: 1 (f=1): [W(1)][15.6%][r=0KiB/s,w=89.1MiB/s][r=0,w=11.4k IOPS][eta 00m:38sJobs: 1 (f=1): [W(1)][17.4%][r=0KiB/s,w=75.8MiB/s][r=0,w=9700 IOPS][eta 00m:38s]Jobs: 1 (f=1): [W(1)][19.6%][r=0KiB/s,w=86.8MiB/s][r=0,w=11.1k IOPS][eta 00m:37sJobs: 1 (f=1): [W(1)][21.3%][r=0KiB/s,w=79.2MiB/s][r=0,w=10.1k IOPS][eta 00m:37sJobs: 1 (f=1): [W(1)][23.4%][r=0KiB/s,w=76.6MiB/s][r=0,w=9801 IOPS][eta 00m:36s]Jobs: 1 (f=1): [W(1)][25.5%][r=0KiB/s,w=80.8MiB/s][r=0,w=10.3k IOPS][eta 00m:35sJobs: 1 (f=1): [W(1)][27.7%][r=0KiB/s,w=86.6MiB/s][r=0,w=11.1k IOPS][eta 00m:34sJobs: 1 (f=1): [W(1)][29.2%][r=0KiB/s,w=78.2MiB/s][r=0,w=10.0k IOPS][eta 00m:34sJobs: 1 (f=1): [W(1)][31.2%][r=0KiB/s,w=84.1MiB/s][r=0,w=10.8k IOPS][eta 00m:33sJobs: 1 (f=1): [W(1)][33.3%][r=0KiB/s,w=72.2MiB/s][r=0,w=9242 IOPS][eta 00m:32s]Jobs: 1 (f=1): [W(1)][35.4%][r=0KiB/s,w=93.6MiB/s][r=0,w=11.0k IOPS][eta 00m:31sJobs: 1 (f=1): [W(1)][38.3%][r=0KiB/s,w=100MiB/s][r=0,w=12.8k IOPS][eta 00m:29s]Jobs: 1 (f=1): [W(1)][40.4%][r=0KiB/s,w=89.5MiB/s][r=0,w=11.5k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][42.6%][r=0KiB/s,w=80.4MiB/s][r=0,w=10.3k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][43.8%][r=0KiB/s,w=82.2MiB/s][r=0,w=10.5k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][45.8%][r=0KiB/s,w=83.1MiB/s][r=0,w=10.6k IOPS][eta 00m:26sJobs: 1 (f=1): [W(1)][47.9%][r=0KiB/s,w=75.5MiB/s][r=0,w=9664 IOPS][eta 00m:25s]Jobs: 1 (f=1): [W(1)][50.0%][r=0KiB/s,w=89.8MiB/s][r=0,w=11.5k IOPS][eta 00m:24sJobs: 1 (f=1): [W(1)][52.1%][r=0KiB/s,w=73.5MiB/s][r=0,w=9408 IOPS][eta 00m:23s]Jobs: 1 (f=1): [W(1)][58.3%][r=0KiB/s,w=78.8MiB/s][r=0,w=10.1k IOPS][eta 00m:20sJobs: 1 (f=1): [W(1)][60.4%][r=0KiB/s,w=82.5MiB/s][r=0,w=10.6k IOPS][eta 00m:19sJobs: 1 (f=1): [W(1)][61.2%][r=0KiB/s,w=79.8MiB/s][r=0,w=10.2k IOPS][eta 00m:19sJobs: 1 (f=1): [W(1)][63.3%][r=0KiB/s,w=83.5MiB/s][r=0,w=10.7k IOPS][eta 00m:18sJobs: 1 (f=1): [W(1)][65.3%][r=0KiB/s,w=82.3MiB/s][r=0,w=10.5k IOPS][eta 00m:17sJobs: 1 (f=1): [W(1)][68.8%][r=0KiB/s,w=88.8MiB/s][r=0,w=11.4k IOPS][eta 00m:15sJobs: 1 (f=1): [W(1)][69.4%][r=0KiB/s,w=75.8MiB/s][r=0,w=9696 IOPS][eta 00m:15s]Jobs: 1 (f=1): [W(1)][71.4%][r=0KiB/s,w=80.3MiB/s][r=0,w=10.3k IOPS][eta 00m:14sJobs: 1 (f=1): [W(1)][73.5%][r=0KiB/s,w=78.5MiB/s][r=0,w=10.0k IOPS][eta 00m:13sJobs: 1 (f=1): [W(1)][75.5%][r=0KiB/s,w=72.3MiB/s][r=0,w=9250 IOPS][eta 00m:12s]Jobs: 1 (f=1): [W(1)][77.6%][r=0KiB/s,w=79.6MiB/s][r=0,w=10.2k IOPS][eta 00m:11sJobs: 1 (f=1): [W(1)][79.6%][r=0KiB/s,w=67.1MiB/s][r=0,w=8584 IOPS][eta 00m:10s]Jobs: 1 (f=1): [W(1)][81.6%][r=0KiB/s,w=80.8MiB/s][r=0,w=10.3k IOPS][eta 00m:09sJobs: 1 (f=1): [W(1)][83.7%][r=0KiB/s,w=64.5MiB/s][r=0,w=8259 IOPS][eta 00m:08s]Jobs: 1 (f=1): [W(1)][98.0%][r=0KiB/s,w=78.8MiB/s][r=0,w=10.1k IOPS][eta 00m:01sJobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=66.3MiB/s][r=0,w=8488 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4916: Thu Oct  5 18:04:27 2017
  write: IOPS=10.1k, BW=79.3MiB/s (83.1MB/s)(4096MiB/51675msec)
    slat (nsec): min=263, max=304778, avg=858.66, stdev=729.90
    clat (usec): min=2138, max=13649, avg=3135.99, stdev=641.69
     lat (usec): min=2139, max=13651, avg=3136.84, stdev=641.79
    clat percentiles (usec):
     |  1.00th=[ 2245],  5.00th=[ 2343], 10.00th=[ 2442], 20.00th=[ 2606],
     | 30.00th=[ 2737], 40.00th=[ 2900], 50.00th=[ 3032], 60.00th=[ 3195],
     | 70.00th=[ 3359], 80.00th=[ 3589], 90.00th=[ 3949], 95.00th=[ 4228],
     | 99.00th=[ 4883], 99.50th=[ 5080], 99.90th=[ 6259], 99.95th=[11731],
     | 99.99th=[13435]
   bw (  KiB/s): min=57856, max=105472, per=100.00%, avg=81204.37, stdev=10709.33, samples=103
   iops        : min= 7232, max=13184, avg=10150.52, stdev=1338.68, samples=103
  lat (msec)   : 4=91.02%, 10=8.92%, 20=0.06%
  cpu          : usr=3.23%, sys=1.35%, ctx=262209, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,524288,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=79.3MiB/s (83.1MB/s), 79.3MiB/s-79.3MiB/s (83.1MB/s-83.1MB/s), io=4096MiB (4295MB), run=51675-51675msec

Disk stats (read/write):
  sda: ios=0/524002, merge=0/84, ticks=0/31620, in_queue=31437, util=58.85%
```

*file-size*
```
ls -al test8K 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 18:04 test8K
```

*reads*
```
./fio --filename=test8K --rw=read --ioengine=posixaio --direct=1 --blocksize=8K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 8192B-8192B, (W) 8192B-8192B, (T) 8192B-8192B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][17.1%][r=98.1MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][19.0%][r=80.2MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][21.4%][r=94.8MiB/s,w=0KiB/s][r=12.1k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][23.8%][r=101MiB/s,w=0KiB/s][r=12.9k,w=0 IOPS][eta 00m:32s]Jobs: 1 (f=1): [R(1)][26.2%][r=87.1MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][27.9%][r=85.5MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][30.2%][r=85.8MiB/s,w=0KiB/s][r=10.0k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][33.3%][r=112MiB/s,w=0KiB/s][r=14.4k,w=0 IOPS][eta 00m:28s]Jobs: 1 (f=1): [R(1)][38.1%][r=92.2MiB/s,w=0KiB/s][r=11.8k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][40.5%][r=102MiB/s,w=0KiB/s][r=13.1k,w=0 IOPS][eta 00m:25s]Jobs: 1 (f=1): [R(1)][42.9%][r=80.8MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [R(1)][45.2%][r=81.1MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][47.6%][r=89.8MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][48.8%][r=87.6MiB/s,w=0KiB/s][r=11.2k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][51.2%][r=80.2MiB/s,w=0KiB/s][r=10.3k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][53.5%][r=77.1MiB/s,w=0KiB/s][r=9865,w=0 IOPS][eta 00m:20s]Jobs: 1 (f=1): [R(1)][55.8%][r=96.0MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [R(1)][58.1%][r=109MiB/s,w=0KiB/s][r=13.0k,w=0 IOPS][eta 00m:18s]Jobs: 1 (f=1): [R(1)][60.5%][r=90.2MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][62.8%][r=105MiB/s,w=0KiB/s][r=13.5k,w=0 IOPS][eta 00m:16s]Jobs: 1 (f=1): [R(1)][67.4%][r=81.3MiB/s,w=0KiB/s][r=10.4k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][69.8%][r=86.0MiB/s,w=0KiB/s][r=11.0k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [R(1)][72.1%][r=89.6MiB/s,w=0KiB/s][r=11.5k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [R(1)][74.4%][r=106MiB/s,w=0KiB/s][r=13.6k,w=0 IOPS][eta 00m:11s]Jobs: 1 (f=1): [R(1)][76.7%][r=98.3MiB/s,w=0KiB/s][r=12.6k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][79.1%][r=85.5MiB/s,w=0KiB/s][r=10.9k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][81.4%][r=87.1MiB/s,w=0KiB/s][r=11.1k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][83.7%][r=80.0MiB/s,w=0KiB/s][r=10.2k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [R(1)][86.0%][r=82.1MiB/s,w=0KiB/s][r=10.5k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][86.4%][r=84.5MiB/s,w=0KiB/s][r=10.8k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][88.6%][r=89.3MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [R(1)][90.9%][r=88.8MiB/s,w=0KiB/s][r=11.4k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [R(1)][93.2%][r=95.8MiB/s,w=0KiB/s][r=12.3k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [R(1)][95.5%][r=90.5MiB/s,w=0KiB/s][r=11.6k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [R(1)][100.0%][r=119MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=4923: Thu Oct  5 18:05:22 2017
   read: IOPS=12.0k, BW=93.9MiB/s (98.5MB/s)(4096MiB/43615msec)
    slat (nsec): min=196, max=152096, avg=480.21, stdev=478.32
    clat (usec): min=1814, max=7478, avg=2648.90, stdev=536.76
     lat (usec): min=1814, max=7478, avg=2649.38, stdev=536.85
    clat percentiles (usec):
     |  1.00th=[ 1909],  5.00th=[ 1975], 10.00th=[ 2040], 20.00th=[ 2147],
     | 30.00th=[ 2278], 40.00th=[ 2409], 50.00th=[ 2540], 60.00th=[ 2704],
     | 70.00th=[ 2900], 80.00th=[ 3097], 90.00th=[ 3392], 95.00th=[ 3654],
     | 99.00th=[ 4146], 99.50th=[ 4359], 99.90th=[ 4817], 99.95th=[ 5145],
     | 99.99th=[ 5997]
   bw (  KiB/s): min=72192, max=128000, per=99.94%, avg=96109.71, stdev=13975.50, samples=87
   iops        : min= 9024, max=16000, avg=12013.71, stdev=1746.94, samples=87
  lat (msec)   : 2=7.26%, 4=91.03%, 10=1.70%
  cpu          : usr=3.03%, sys=1.60%, ctx=262199, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=524288,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=93.9MiB/s (98.5MB/s), 93.9MiB/s-93.9MiB/s (98.5MB/s-98.5MB/s), io=4096MiB (4295MB), run=43615-43615msec

Disk stats (read/write):
  sda: ios=521204/4, merge=0/7, ticks=26660/53, in_queue=26520, util=60.91%
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

