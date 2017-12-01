# fio results (all on ubuntu 16.04 x64)
```
# sequential writes
fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob

# sequential reads
fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
```

## aws ec2 micro - 990M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            488M     0  488M   0% /dev
tmpfs           100M   11M   89M  11% /run
/dev/xvda1      7.7G  2.2G  5.6G  28% /
tmpfs           496M     0  496M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           496M     0  496M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=11.0MiB/s][r=0,w=3062 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=21461: Fri Oct  6 05:21:27 2017
  write: IOPS=3068, BW=11.0MiB/s (12.6MB/s)(4096MiB/341704msec)
    slat (usec): min=2, max=1841, avg= 7.63, stdev= 5.14
    clat (usec): min=359, max=45445, avg=1294.12, stdev=1983.67
     lat (usec): min=371, max=45453, avg=1301.99, stdev=1983.73
    clat percentiles (usec):
     |  1.00th=[  445],  5.00th=[  482], 10.00th=[  506], 20.00th=[  553],
     | 30.00th=[  603], 40.00th=[  725], 50.00th=[ 1188], 60.00th=[ 1254],
     | 70.00th=[ 1287], 80.00th=[ 1319], 90.00th=[ 1369], 95.00th=[ 1467],
     | 99.00th=[13435], 99.50th=[14222], 99.90th=[18482], 99.95th=[21627],
     | 99.99th=[28181]
   bw (  KiB/s): min=10184, max=22720, per=99.99%, avg=12272.61, stdev=619.59, samples=683
   iops        : min= 2546, max= 5680, avg=3068.10, stdev=154.90, samples=683
  lat (usec)   : 500=8.64%, 750=32.36%, 1000=5.42%
  lat (msec)   : 2=49.38%, 4=1.38%, 10=0.63%, 20=2.12%, 50=0.07%
  cpu          : usr=0.74%, sys=2.67%, ctx=1010654, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=11.0MiB/s (12.6MB/s), 11.0MiB/s-11.0MiB/s (12.6MB/s-12.6MB/s), io=4096MiB (4295MB), run=341704-341704msec

Disk stats (read/write):
  xvda: ios=0/1048453, merge=0/110, ticks=0/1362220, in_queue=1362208, util=100.00%
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:21 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=11.0MiB/s,w=0KiB/s][r=3062,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=21485: Fri Oct  6 05:28:47 2017
   read: IOPS=3070, BW=11.0MiB/s (12.6MB/s)(3598MiB/300002msec)
    slat (nsec): min=1430, max=176505, avg=5769.66, stdev=1735.12
    clat (usec): min=286, max=18819, avg=1295.46, stdev=502.84
     lat (usec): min=291, max=18825, avg=1301.45, stdev=502.82
    clat percentiles (usec):
     |  1.00th=[  367],  5.00th=[  465], 10.00th=[ 1172], 20.00th=[ 1254],
     | 30.00th=[ 1270], 40.00th=[ 1287], 50.00th=[ 1303], 60.00th=[ 1303],
     | 70.00th=[ 1319], 80.00th=[ 1336], 90.00th=[ 1369], 95.00th=[ 1418],
     | 99.00th=[ 3392], 99.50th=[ 4293], 99.90th=[ 6915], 99.95th=[ 8717],
     | 99.99th=[11994]
   bw (  KiB/s): min= 9008, max=36720, per=99.99%, avg=12278.93, stdev=1103.92, samples=600
   iops        : min= 2252, max= 9180, avg=3069.70, stdev=275.98, samples=600
  lat (usec)   : 500=5.73%, 750=1.42%, 1000=1.22%
  lat (msec)   : 2=88.88%, 4=2.12%, 10=0.60%, 20=0.03%
  cpu          : usr=1.13%, sys=2.78%, ctx=905007, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=921030,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=11.0MiB/s (12.6MB/s), 11.0MiB/s-11.0MiB/s (12.6MB/s-12.6MB/s), io=3598MiB (3773MB), run=300002-300002msec

Disk stats (read/write):
  xvda: ios=920720/20, merge=0/6, ticks=1195468/8, in_queue=1195472, util=100.00%
```

## gcloud micro - 585M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            286M     0  286M   0% /dev
tmpfs            59M  6.5M   53M  11% /run
/dev/sda1        30G  2.4G   27G   9% /
tmpfs           294M     0  294M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           294M     0  294M   0% /sys/fs/cgroup
tmpfs            59M     0   59M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=16.1MiB/s][r=0,w=4133 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2663: Fri Oct  6 05:20:04 2017
  write: IOPS=5030, BW=19.6MiB/s (20.6MB/s)(4096MiB/208446msec)
    slat (usec): min=5, max=4895, avg=17.37, stdev=11.51
    clat (usec): min=72, max=17977, avg=775.18, stdev=548.82
     lat (usec): min=419, max=17994, avg=792.92, stdev=548.73
    clat percentiles (usec):
     |  1.00th=[  490],  5.00th=[  523], 10.00th=[  545], 20.00th=[  570],
     | 30.00th=[  594], 40.00th=[  619], 50.00th=[  644], 60.00th=[  668],
     | 70.00th=[  717], 80.00th=[  799], 90.00th=[ 1029], 95.00th=[ 1418],
     | 99.00th=[ 3261], 99.50th=[ 5276], 99.90th=[ 6063], 99.95th=[ 6718],
     | 99.99th=[10683]
   bw (  KiB/s): min=13360, max=24367, per=100.00%, avg=20129.69, stdev=2198.92, samples=416
   iops        : min= 3340, max= 6091, avg=5032.39, stdev=549.74, samples=416
  lat (usec)   : 100=0.01%, 250=0.01%, 500=1.78%, 750=73.47%, 1000=14.03%
  lat (msec)   : 2=8.29%, 4=1.69%, 10=0.74%, 20=0.01%
  cpu          : usr=2.06%, sys=9.08%, ctx=726298, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=19.6MiB/s (20.6MB/s), 19.6MiB/s-19.6MiB/s (20.6MB/s-20.6MB/s), io=4096MiB (4295MB), run=208446-208446msec

Disk stats (read/write):
  sda: ios=11/1047952, merge=0/192, ticks=104/786404, in_queue=786132, util=99.71%
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:20 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=15.8MiB/s,w=0KiB/s][r=4053,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2692: Fri Oct  6 05:28:28 2017
   read: IOPS=3846, BW=15.0MiB/s (15.8MB/s)(4096MiB/272605msec)
    slat (usec): min=3, max=2377, avg=13.46, stdev= 7.43
    clat (usec): min=34, max=103150, avg=1023.88, stdev=2824.52
     lat (usec): min=307, max=103162, avg=1037.67, stdev=2824.36
    clat percentiles (usec):
     |  1.00th=[  355],  5.00th=[  383], 10.00th=[  396], 20.00th=[  420],
     | 30.00th=[  441], 40.00th=[  461], 50.00th=[  486], 60.00th=[  529],
     | 70.00th=[  603], 80.00th=[  799], 90.00th=[ 1549], 95.00th=[ 2057],
     | 99.00th=[15401], 99.50th=[22152], 99.90th=[36963], 99.95th=[44303],
     | 99.99th=[60031]
   bw (  KiB/s): min= 8664, max=20968, per=99.99%, avg=15384.84, stdev=1360.44, samples=545
   iops        : min= 2166, max= 5242, avg=3846.20, stdev=340.11, samples=545
  lat (usec)   : 50=0.01%, 100=0.01%, 250=0.01%, 500=54.15%, 750=24.11%
  lat (usec)   : 1000=6.15%
  lat (msec)   : 2=10.41%, 4=2.87%, 10=0.78%, 20=0.91%, 50=0.59%
  lat (msec)   : 100=0.03%, 250=0.01%
  cpu          : usr=2.03%, sys=7.34%, ctx=913027, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=15.0MiB/s (15.8MB/s), 15.0MiB/s-15.0MiB/s (15.8MB/s-15.8MB/s), io=4096MiB (4295MB), run=272605-272605msec

Disk stats (read/write):
  sda: ios=1047498/60, merge=0/41, ticks=1065944/428, in_queue=1066052, util=100.00%
```

## vultr - 488M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            225M     0  225M   0% /dev
tmpfs            49M  5.6M   44M  12% /run
/dev/vda1        20G  7.9G   11G  43% /
tmpfs           245M     0  245M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           245M     0  245M   0% /sys/fs/cgroup
tmpfs            49M     0   49M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=119MiB/s][r=0,w=30.4k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14283: Fri Oct  6 05:16:28 2017
  write: IOPS=28.8k, BW=112MiB/s (118MB/s)(4096MiB/36447msec)
    slat (usec): min=2, max=6987, avg=11.73, stdev=13.87
    clat (usec): min=19, max=13083, avg=124.72, stdev=96.63
     lat (usec): min=50, max=13090, avg=136.97, stdev=97.07
    clat percentiles (usec):
     |  1.00th=[   53],  5.00th=[   62], 10.00th=[   69], 20.00th=[   78],
     | 30.00th=[   86], 40.00th=[   94], 50.00th=[  103], 60.00th=[  114],
     | 70.00th=[  128], 80.00th=[  149], 90.00th=[  202], 95.00th=[  273],
     | 99.00th=[  408], 99.50th=[  457], 99.90th=[  676], 99.95th=[ 1004],
     | 99.99th=[ 2966]
   bw (  KiB/s): min=97432, max=138208, per=99.99%, avg=115065.11, stdev=7765.68, samples=72
   iops        : min=24358, max=34552, avg=28766.28, stdev=1941.42, samples=72
  lat (usec)   : 20=0.01%, 50=0.44%, 100=46.39%, 250=46.92%, 500=5.94%
  lat (usec)   : 750=0.23%, 1000=0.03%
  lat (msec)   : 2=0.03%, 4=0.01%, 10=0.01%, 20=0.01%
  cpu          : usr=6.57%, sys=33.58%, ctx=696856, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=112MiB/s (118MB/s), 112MiB/s-112MiB/s (118MB/s-118MB/s), io=4096MiB (4295MB), run=36447-36447msec

Disk stats (read/write):
  vda: ios=0/1047072, merge=0/86, ticks=0/107356, in_queue=107100, util=96.07%
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:16 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][10.5%][r=72.6MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [R(1)][12.5%][r=86.5MiB/s,w=0KiB/s][r=22.1k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [R(1)][14.3%][r=68.3MiB/s,w=0KiB/s][r=17.5k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [R(1)][16.1%][r=69.2MiB/s,w=0KiB/s][r=17.7k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [R(1)][17.5%][r=68.9MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [R(1)][19.6%][r=77.0MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [R(1)][21.4%][r=69.4MiB/s,w=0KiB/s][r=17.8k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [R(1)][23.2%][r=70.5MiB/s,w=0KiB/s][r=18.1k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [R(1)][24.6%][r=68.8MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [R(1)][26.8%][r=74.3MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][28.1%][r=67.8MiB/s,w=0KiB/s][r=17.4k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][29.8%][r=73.4MiB/s,w=0KiB/s][r=18.8k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [R(1)][32.1%][r=79.3MiB/s,w=0KiB/s][r=20.3k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [R(1)][33.9%][r=69.2MiB/s,w=0KiB/s][r=17.7k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [R(1)][35.7%][r=69.0MiB/s,w=0KiB/s][r=17.9k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][37.5%][r=72.5MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [R(1)][39.3%][r=71.0MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][41.1%][r=77.1MiB/s,w=0KiB/s][r=19.7k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][42.9%][r=68.9MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][44.6%][r=74.7MiB/s,w=0KiB/s][r=19.1k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][45.6%][r=66.3MiB/s,w=0KiB/s][r=16.0k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][47.4%][r=67.3MiB/s,w=0KiB/s][r=17.2k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][49.1%][r=68.6MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][50.9%][r=75.6MiB/s,w=0KiB/s][r=19.3k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [R(1)][52.6%][r=75.1MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][55.4%][r=75.0MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [R(1)][56.1%][r=68.3MiB/s,w=0KiB/s][r=17.5k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [R(1)][58.9%][r=76.8MiB/s,w=0KiB/s][r=19.6k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][60.7%][r=71.3MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][62.5%][r=72.5MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][64.3%][r=71.4MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [R(1)][66.1%][r=69.8MiB/s,w=0KiB/s][r=17.9k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [R(1)][67.9%][r=73.8MiB/s,w=0KiB/s][r=18.9k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][69.6%][r=72.2MiB/s,w=0KiB/s][r=18.5k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][71.4%][r=72.5MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [R(1)][73.2%][r=73.3MiB/s,w=0KiB/s][r=18.8k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [R(1)][75.0%][r=68.5MiB/s,w=0KiB/s][r=17.5k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][75.4%][r=67.0MiB/s,w=0KiB/s][r=17.2k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][77.2%][r=66.5MiB/s,w=0KiB/s][r=17.0k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [R(1)][78.9%][r=66.2MiB/s,w=0KiB/s][r=16.9k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [R(1)][80.7%][r=67.3MiB/s,w=0KiB/s][r=17.2k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [R(1)][82.5%][r=66.1MiB/s,w=0KiB/s][r=16.9k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][84.2%][r=68.8MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][86.0%][r=79.7MiB/s,w=0KiB/s][r=20.4k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][87.7%][r=70.7MiB/s,w=0KiB/s][r=18.1k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [R(1)][89.5%][r=67.6MiB/s,w=0KiB/s][r=17.3k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][91.2%][r=71.4MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [R(1)][93.0%][r=74.1MiB/s,w=0KiB/s][r=18.0k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [R(1)][94.7%][r=71.4MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [R(1)][96.5%][r=69.3MiB/s,w=0KiB/s][r=17.7k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [R(1)][98.2%][r=69.8MiB/s,w=0KiB/s][r=17.9k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [R(1)][100.0%][r=56.5MiB/s,w=0KiB/s][r=14.5k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14296: Fri Oct  6 05:19:10 2017
   read: IOPS=18.2k, BW=70.9MiB/s (74.4MB/s)(4096MiB/57747msec)
    slat (nsec): min=1412, max=15163k, avg=8012.56, stdev=20328.96
    clat (usec): min=16, max=15325, avg=210.11, stdev=159.08
     lat (usec): min=53, max=15333, avg=218.59, stdev=160.45
    clat percentiles (usec):
     |  1.00th=[   76],  5.00th=[   99], 10.00th=[  112], 20.00th=[  147],
     | 30.00th=[  167], 40.00th=[  182], 50.00th=[  192], 60.00th=[  204],
     | 70.00th=[  219], 80.00th=[  241], 90.00th=[  289], 95.00th=[  343],
     | 99.00th=[  742], 99.50th=[ 1221], 99.90th=[ 1942], 99.95th=[ 2278],
     | 99.99th=[ 4555]
   bw (  KiB/s): min=55456, max=91256, per=100.00%, avg=72724.08, stdev=5577.55, samples=115
   iops        : min=13864, max=22814, avg=18181.00, stdev=1394.39, samples=115
  lat (usec)   : 20=0.01%, 50=0.02%, 100=5.20%, 250=77.36%, 500=15.78%
  lat (usec)   : 750=0.66%, 1000=0.30%
  lat (msec)   : 2=0.60%, 4=0.07%, 10=0.01%, 20=0.01%
  cpu          : usr=5.38%, sys=20.70%, ctx=514925, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=70.9MiB/s (74.4MB/s), 70.9MiB/s-70.9MiB/s (74.4MB/s-74.4MB/s), io=4096MiB (4295MB), run=57747-57747msec

Disk stats (read/write):
  vda: ios=1047349/23, merge=0/25, ticks=205260/0, in_queue=204968, util=97.78%
```

## linode - 989M
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        20G  1.3G   18G   7% /
devtmpfs        493M     0  493M   0% /dev
tmpfs           495M     0  495M   0% /dev/shm
tmpfs           495M  7.7M  488M   2% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           495M     0  495M   0% /sys/fs/cgroup
tmpfs            99M     0   99M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=123MiB/s][r=0,w=31.6k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=13990: Fri Oct  6 05:16:30 2017
  write: IOPS=30.3k, BW=118MiB/s (124MB/s)(4096MiB/34635msec)
    slat (usec): min=3, max=8280, avg=14.89, stdev=28.04
    clat (usec): min=15, max=8540, avg=114.23, stdev=57.89
     lat (usec): min=57, max=8566, avg=129.77, stdev=64.26
    clat percentiles (usec):
     |  1.00th=[   37],  5.00th=[   78], 10.00th=[   84], 20.00th=[   91],
     | 30.00th=[   97], 40.00th=[  102], 50.00th=[  109], 60.00th=[  116],
     | 70.00th=[  123], 80.00th=[  135], 90.00th=[  153], 95.00th=[  172],
     | 99.00th=[  219], 99.50th=[  239], 99.90th=[  318], 99.95th=[  420],
     | 99.99th=[ 1582]
   bw (  KiB/s): min=92096, max=145360, per=99.97%, avg=121063.36, stdev=11857.39, samples=69
   iops        : min=23024, max=36340, avg=30265.83, stdev=2964.34, samples=69
  lat (usec)   : 20=0.04%, 50=1.83%, 100=34.36%, 250=63.43%, 500=0.31%
  lat (usec)   : 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=7.20%, sys=44.01%, ctx=319687, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=118MiB/s (124MB/s), 118MiB/s-118MiB/s (124MB/s-124MB/s), io=4096MiB (4295MB), run=34635-34635msec

Disk stats (read/write):
  sda: ios=0/1040843, merge=0/50, ticks=0/53280, in_queue=52957, util=64.13%
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:16 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=158MiB/s,w=0KiB/s][r=40.4k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=13999: Fri Oct  6 05:18:26 2017
   read: IOPS=39.0k, BW=152MiB/s (160MB/s)(4096MiB/26880msec)
    slat (usec): min=2, max=2958, avg= 6.90, stdev= 9.81
    clat (nsec): min=1152, max=7695.3k, avg=93644.19, stdev=42483.12
     lat (usec): min=49, max=7699, avg=100.94, stdev=43.98
    clat percentiles (usec):
     |  1.00th=[   56],  5.00th=[   69], 10.00th=[   73], 20.00th=[   78],
     | 30.00th=[   82], 40.00th=[   85], 50.00th=[   90], 60.00th=[   94],
     | 70.00th=[  100], 80.00th=[  108], 90.00th=[  119], 95.00th=[  133],
     | 99.00th=[  165], 99.50th=[  186], 99.90th=[  285], 99.95th=[  404],
     | 99.99th=[ 1532]
   bw (  KiB/s): min=111000, max=180696, per=100.00%, avg=156126.19, stdev=16499.95, samples=53
   iops        : min=27750, max=45174, avg=39031.55, stdev=4124.99, samples=53
  lat (usec)   : 2=0.01%, 20=0.12%, 50=0.61%, 100=69.36%, 250=29.77%
  lat (usec)   : 500=0.11%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=7.19%, sys=31.37%, ctx=263893, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=152MiB/s (160MB/s), 152MiB/s-152MiB/s (160MB/s-160MB/s), io=4096MiB (4295MB), run=26880-26880msec

Disk stats (read/write):
  sda: ios=1039878/0, merge=0/0, ticks=40360/0, in_queue=40120, util=51.45%
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            477M     0  477M   0% /dev
tmpfs           100M  5.4M   94M   6% /run
/dev/vda1        30G  1.8G   27G   7% /
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           497M     0  497M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][10.9%][r=0KiB/s,w=61.6MiB/s][r=0,w=15.8k IOPS][eta 00m:49sJobs: 1 (f=1): [W(1)][12.5%][r=0KiB/s,w=69.3MiB/s][r=0,w=17.8k IOPS][eta 00m:49sJobs: 1 (f=1): [W(1)][14.5%][r=0KiB/s,w=82.5MiB/s][r=0,w=21.1k IOPS][eta 00m:47sJobs: 1 (f=1): [W(1)][16.7%][r=0KiB/s,w=78.2MiB/s][r=0,w=20.0k IOPS][eta 00m:45sJobs: 1 (f=1): [W(1)][18.2%][r=0KiB/s,w=65.3MiB/s][r=0,w=16.7k IOPS][eta 00m:45sJobs: 1 (f=1): [W(1)][20.0%][r=0KiB/s,w=67.5MiB/s][r=0,w=17.3k IOPS][eta 00m:44sJobs: 1 (f=1): [W(1)][21.8%][r=0KiB/s,w=73.7MiB/s][r=0,w=18.9k IOPS][eta 00m:43sJobs: 1 (f=1): [W(1)][23.2%][r=0KiB/s,w=70.4MiB/s][r=0,w=18.0k IOPS][eta 00m:43sJobs: 1 (f=1): [W(1)][25.0%][r=0KiB/s,w=74.1MiB/s][r=0,w=18.0k IOPS][eta 00m:42sJobs: 1 (f=1): [W(1)][26.8%][r=0KiB/s,w=58.7MiB/s][r=0,w=15.0k IOPS][eta 00m:41sJobs: 1 (f=1): [W(1)][28.1%][r=0KiB/s,w=61.1MiB/s][r=0,w=15.6k IOPS][eta 00m:41sJobs: 1 (f=1): [W(1)][30.4%][r=0KiB/s,w=90.8MiB/s][r=0,w=23.2k IOPS][eta 00m:39sJobs: 1 (f=1): [W(1)][32.1%][r=0KiB/s,w=82.2MiB/s][r=0,w=21.0k IOPS][eta 00m:38sJobs: 1 (f=1): [W(1)][33.9%][r=0KiB/s,w=68.2MiB/s][r=0,w=17.5k IOPS][eta 00m:37sJobs: 1 (f=1): [W(1)][35.7%][r=0KiB/s,w=57.4MiB/s][r=0,w=14.7k IOPS][eta 00m:36sJobs: 1 (f=1): [W(1)][36.8%][r=0KiB/s,w=58.1MiB/s][r=0,w=14.9k IOPS][eta 00m:36sJobs: 1 (f=1): [W(1)][38.6%][r=0KiB/s,w=55.1MiB/s][r=0,w=14.1k IOPS][eta 00m:35sJobs: 1 (f=1): [W(1)][39.7%][r=0KiB/s,w=60.7MiB/s][r=0,w=15.5k IOPS][eta 00m:35sJobs: 1 (f=1): [W(1)][41.4%][r=0KiB/s,w=69.8MiB/s][r=0,w=17.9k IOPS][eta 00m:34sJobs: 1 (f=1): [W(1)][43.1%][r=0KiB/s,w=70.4MiB/s][r=0,w=18.0k IOPS][eta 00m:33sJobs: 1 (f=1): [W(1)][44.8%][r=0KiB/s,w=57.6MiB/s][r=0,w=14.7k IOPS][eta 00m:32sJobs: 1 (f=1): [W(1)][46.6%][r=0KiB/s,w=70.8MiB/s][r=0,w=18.1k IOPS][eta 00m:31sJobs: 1 (f=1): [W(1)][47.5%][r=0KiB/s,w=56.1MiB/s][r=0,w=14.4k IOPS][eta 00m:31sJobs: 1 (f=1): [W(1)][49.2%][r=0KiB/s,w=56.9MiB/s][r=0,w=14.6k IOPS][eta 00m:30sJobs: 1 (f=1): [W(1)][50.8%][r=0KiB/s,w=77.1MiB/s][r=0,w=19.7k IOPS][eta 00m:29sJobs: 1 (f=1): [W(1)][52.5%][r=0KiB/s,w=63.4MiB/s][r=0,w=16.2k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][55.2%][r=0KiB/s,w=84.0MiB/s][r=0,w=21.8k IOPS][eta 00m:26sJobs: 1 (f=1): [W(1)][56.9%][r=0KiB/s,w=72.0MiB/s][r=0,w=18.7k IOPS][eta 00m:25sJobs: 1 (f=1): [W(1)][57.6%][r=0KiB/s,w=61.4MiB/s][r=0,w=15.7k IOPS][eta 00m:25sJobs: 1 (f=1): [W(1)][60.3%][r=0KiB/s,w=75.1MiB/s][r=0,w=19.2k IOPS][eta 00m:23sJobs: 1 (f=1): [W(1)][62.1%][r=0KiB/s,w=84.2MiB/s][r=0,w=21.6k IOPS][eta 00m:22sJobs: 1 (f=1): [W(1)][63.8%][r=0KiB/s,w=75.0MiB/s][r=0,w=19.2k IOPS][eta 00m:21sJobs: 1 (f=1): [W(1)][65.5%][r=0KiB/s,w=66.8MiB/s][r=0,w=17.1k IOPS][eta 00m:20sJobs: 1 (f=1): [W(1)][67.2%][r=0KiB/s,w=64.9MiB/s][r=0,w=16.6k IOPS][eta 00m:19sJobs: 1 (f=1): [W(1)][69.0%][r=0KiB/s,w=69.0MiB/s][r=0,w=17.7k IOPS][eta 00m:18sJobs: 1 (f=1): [W(1)][70.7%][r=0KiB/s,w=71.7MiB/s][r=0,w=18.4k IOPS][eta 00m:17sJobs: 1 (f=1): [W(1)][72.4%][r=0KiB/s,w=87.0MiB/s][r=0,w=22.3k IOPS][eta 00m:16sJobs: 1 (f=1): [W(1)][74.1%][r=0KiB/s,w=86.4MiB/s][r=0,w=22.1k IOPS][eta 00m:15sJobs: 1 (f=1): [W(1)][75.9%][r=0KiB/s,w=57.1MiB/s][r=0,w=14.6k IOPS][eta 00m:14sJobs: 1 (f=1): [W(1)][77.6%][r=0KiB/s,w=71.8MiB/s][r=0,w=18.4k IOPS][eta 00m:13sJobs: 1 (f=1): [W(1)][79.3%][r=0KiB/s,w=64.1MiB/s][r=0,w=16.4k IOPS][eta 00m:12sJobs: 1 (f=1): [W(1)][81.0%][r=0KiB/s,w=73.5MiB/s][r=0,w=18.8k IOPS][eta 00m:11sJobs: 1 (f=1): [W(1)][82.8%][r=0KiB/s,w=70.1MiB/s][r=0,w=17.9k IOPS][eta 00m:10sJobs: 1 (f=1): [W(1)][84.5%][r=0KiB/s,w=66.2MiB/s][r=0,w=16.0k IOPS][eta 00m:09sJobs: 1 (f=1): [W(1)][86.2%][r=0KiB/s,w=66.4MiB/s][r=0,w=17.0k IOPS][eta 00m:08sJobs: 1 (f=1): [W(1)][87.9%][r=0KiB/s,w=59.1MiB/s][r=0,w=15.1k IOPS][eta 00m:07sJobs: 1 (f=1): [W(1)][89.7%][r=0KiB/s,w=49.4MiB/s][r=0,w=12.7k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][89.8%][r=0KiB/s,w=63.7MiB/s][r=0,w=16.3k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][91.5%][r=0KiB/s,w=59.1MiB/s][r=0,w=15.1k IOPS][eta 00m:05sJobs: 1 (f=1): [W(1)][93.2%][r=0KiB/s,w=68.2MiB/s][r=0,w=17.5k IOPS][eta 00m:04sJobs: 1 (f=1): [W(1)][94.9%][r=0KiB/s,w=57.8MiB/s][r=0,w=14.8k IOPS][eta 00m:03sJobs: 1 (f=1): [W(1)][96.6%][r=0KiB/s,w=67.6MiB/s][r=0,w=17.3k IOPS][eta 00m:02sJobs: 1 (f=1): [W(1)][98.3%][r=0KiB/s,w=77.4MiB/s][r=0,w=19.8k IOPS][eta 00m:01sJobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=55.7MiB/s][r=0,w=14.3k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19060: Fri Oct  6 05:16:59 2017
  write: IOPS=17.6k, BW=68.9MiB/s (72.2MB/s)(4096MiB/59471msec)
    slat (nsec): min=1888, max=89734k, avg=4931.61, stdev=87669.18
    clat (usec): min=19, max=318768, avg=220.93, stdev=1481.55
     lat (usec): min=74, max=318771, avg=226.04, stdev=1484.23
    clat percentiles (usec):
     |  1.00th=[   96],  5.00th=[  110], 10.00th=[  119], 20.00th=[  130],
     | 30.00th=[  139], 40.00th=[  147], 50.00th=[  155], 60.00th=[  161],
     | 70.00th=[  172], 80.00th=[  196], 90.00th=[  351], 95.00th=[  383],
     | 99.00th=[  725], 99.50th=[ 1319], 99.90th=[ 4146], 99.95th=[ 7242],
     | 99.99th=[87557]
   bw (  KiB/s): min=24192, max=102752, per=100.00%, avg=70616.00, stdev=12039.86, samples=118
   iops        : min= 6048, max=25688, avg=17654.00, stdev=3009.96, samples=118
  lat (usec)   : 20=0.01%, 50=0.01%, 100=1.87%, 250=81.15%, 500=15.18%
  lat (usec)   : 750=0.82%, 1000=0.30%
  lat (msec)   : 2=0.41%, 4=0.15%, 10=0.07%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.02%, 250=0.01%, 500=0.01%
  cpu          : usr=1.88%, sys=9.58%, ctx=462923, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=68.9MiB/s (72.2MB/s), 68.9MiB/s-68.9MiB/s (72.2MB/s-72.2MB/s), io=4096MiB (4295MB), run=59471-59471msec

Disk stats (read/write):
  vda: ios=0/1047346, merge=0/92, ticks=0/217052, in_queue=216876, util=96.68%
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  6 05:16 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=206MiB/s,w=0KiB/s][r=52.7k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=19069: Fri Oct  6 05:17:59 2017
   read: IOPS=47.7k, BW=186MiB/s (195MB/s)(4096MiB/21975msec)
    slat (nsec): min=1218, max=177148, avg=2855.63, stdev=1443.20
    clat (usec): min=16, max=7624, avg=80.17, stdev=35.83
     lat (usec): min=39, max=7631, avg=83.18, stdev=35.83
    clat percentiles (usec):
     |  1.00th=[   54],  5.00th=[   59], 10.00th=[   62], 20.00th=[   67],
     | 30.00th=[   70], 40.00th=[   73], 50.00th=[   77], 60.00th=[   81],
     | 70.00th=[   85], 80.00th=[   91], 90.00th=[  100], 95.00th=[  110],
     | 99.00th=[  143], 99.50th=[  206], 99.90th=[  347], 99.95th=[  506],
     | 99.99th=[ 1319]
   bw (  KiB/s): min=152152, max=214672, per=99.73%, avg=190358.33, stdev=15984.36, samples=43
   iops        : min=38038, max=53668, avg=47589.58, stdev=3996.09, samples=43
  lat (usec)   : 20=0.01%, 50=0.24%, 100=89.52%, 250=10.00%, 500=0.20%
  lat (usec)   : 750=0.03%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=5.19%, sys=19.57%, ctx=467452, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=186MiB/s (195MB/s), 186MiB/s-186MiB/s (195MB/s-195MB/s), io=4096MiB (4295MB), run=21975-21975msec

Disk stats (read/write):
  vda: ios=1044678/2, merge=0/1, ticks=78796/0, in_queue=78700, util=97.42%
```

## ovh sg - 1024M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            476M     0  476M   0% /dev
tmpfs            97M  3.0M   94M   4% /run
/dev/sda1        30G  1.5G   28G   6% /
tmpfs           485M     0  485M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           485M     0  485M   0% /sys/fs/cgroup
tmpfs            97M     0   97M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][10.6%][r=0KiB/s,w=90.8MiB/s][r=0,w=23.2k IOPS][eta 00m:42sJobs: 1 (f=1): [W(1)][12.8%][r=0KiB/s,w=89.6MiB/s][r=0,w=22.9k IOPS][eta 00m:41sJobs: 1 (f=1): [W(1)][14.9%][r=0KiB/s,w=85.7MiB/s][r=0,w=21.9k IOPS][eta 00m:40sJobs: 1 (f=1): [W(1)][17.0%][r=0KiB/s,w=87.5MiB/s][r=0,w=22.4k IOPS][eta 00m:39sJobs: 1 (f=1): [W(1)][19.1%][r=0KiB/s,w=78.2MiB/s][r=0,w=20.0k IOPS][eta 00m:38sJobs: 1 (f=1): [W(1)][20.8%][r=0KiB/s,w=79.7MiB/s][r=0,w=20.4k IOPS][eta 00m:38sJobs: 1 (f=1): [W(1)][22.9%][r=0KiB/s,w=84.0MiB/s][r=0,w=21.5k IOPS][eta 00m:37sJobs: 1 (f=1): [W(1)][25.5%][r=0KiB/s,w=90.9MiB/s][r=0,w=23.3k IOPS][eta 00m:35sJobs: 1 (f=1): [W(1)][27.7%][r=0KiB/s,w=88.6MiB/s][r=0,w=22.7k IOPS][eta 00m:34sJobs: 1 (f=1): [W(1)][29.8%][r=0KiB/s,w=91.0MiB/s][r=0,w=23.3k IOPS][eta 00m:33sJobs: 1 (f=1): [W(1)][31.9%][r=0KiB/s,w=93.3MiB/s][r=0,w=23.9k IOPS][eta 00m:32sJobs: 1 (f=1): [W(1)][34.0%][r=0KiB/s,w=85.1MiB/s][r=0,w=21.8k IOPS][eta 00m:31sJobs: 1 (f=1): [W(1)][36.2%][r=0KiB/s,w=87.4MiB/s][r=0,w=22.4k IOPS][eta 00m:30sJobs: 1 (f=1): [W(1)][38.3%][r=0KiB/s,w=82.9MiB/s][r=0,w=21.2k IOPS][eta 00m:29sJobs: 1 (f=1): [W(1)][40.4%][r=0KiB/s,w=89.3MiB/s][r=0,w=22.9k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][42.6%][r=0KiB/s,w=87.2MiB/s][r=0,w=22.3k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][44.7%][r=0KiB/s,w=86.3MiB/s][r=0,w=22.1k IOPS][eta 00m:26sJobs: 1 (f=1): [W(1)][46.8%][r=0KiB/s,w=84.6MiB/s][r=0,w=21.6k IOPS][eta 00m:25sJobs: 1 (f=1): [W(1)][48.9%][r=0KiB/s,w=83.5MiB/s][r=0,w=21.4k IOPS][eta 00m:24sJobs: 1 (f=1): [W(1)][51.1%][r=0KiB/s,w=89.5MiB/s][r=0,w=22.9k IOPS][eta 00m:23sJobs: 1 (f=1): [W(1)][53.2%][r=0KiB/s,w=86.3MiB/s][r=0,w=22.1k IOPS][eta 00m:22sJobs: 1 (f=1): [W(1)][55.3%][r=0KiB/s,w=84.9MiB/s][r=0,w=21.7k IOPS][eta 00m:21sJobs: 1 (f=1): [W(1)][57.4%][r=0KiB/s,w=91.0MiB/s][r=0,w=23.3k IOPS][eta 00m:20sJobs: 1 (f=1): [W(1)][59.6%][r=0KiB/s,w=81.8MiB/s][r=0,w=20.9k IOPS][eta 00m:19sJobs: 1 (f=1): [W(1)][61.7%][r=0KiB/s,w=96.9MiB/s][r=0,w=24.8k IOPS][eta 00m:18sJobs: 1 (f=1): [W(1)][63.8%][r=0KiB/s,w=92.2MiB/s][r=0,w=23.6k IOPS][eta 00m:17sJobs: 1 (f=1): [W(1)][66.0%][r=0KiB/s,w=85.1MiB/s][r=0,w=21.8k IOPS][eta 00m:16sJobs: 1 (f=1): [W(1)][68.1%][r=0KiB/s,w=87.3MiB/s][r=0,w=22.3k IOPS][eta 00m:15sJobs: 1 (f=1): [W(1)][70.2%][r=0KiB/s,w=88.3MiB/s][r=0,w=22.6k IOPS][eta 00m:14sJobs: 1 (f=1): [W(1)][72.3%][r=0KiB/s,w=86.2MiB/s][r=0,w=22.1k IOPS][eta 00m:13sJobs: 1 (f=1): [W(1)][74.5%][r=0KiB/s,w=86.5MiB/s][r=0,w=22.2k IOPS][eta 00m:12sJobs: 1 (f=1): [W(1)][76.6%][r=0KiB/s,w=84.2MiB/s][r=0,w=21.5k IOPS][eta 00m:11sJobs: 1 (f=1): [W(1)][78.7%][r=0KiB/s,w=78.7MiB/s][r=0,w=20.1k IOPS][eta 00m:10sJobs: 1 (f=1): [W(1)][80.9%][r=0KiB/s,w=77.4MiB/s][r=0,w=19.8k IOPS][eta 00m:09sJobs: 1 (f=1): [W(1)][83.0%][r=0KiB/s,w=90.7MiB/s][r=0,w=23.2k IOPS][eta 00m:08sJobs: 1 (f=1): [W(1)][85.1%][r=0KiB/s,w=91.2MiB/s][r=0,w=23.4k IOPS][eta 00m:07sJobs: 1 (f=1): [W(1)][87.2%][r=0KiB/s,w=89.4MiB/s][r=0,w=22.9k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][89.4%][r=0KiB/s,w=80.9MiB/s][r=0,w=20.7k IOPS][eta 00m:05sJobs: 1 (f=1): [W(1)][91.5%][r=0KiB/s,w=82.0MiB/s][r=0,w=21.0k IOPS][eta 00m:04sJobs: 1 (f=1): [W(1)][93.6%][r=0KiB/s,w=89.3MiB/s][r=0,w=22.9k IOPS][eta 00m:03sJobs: 1 (f=1): [W(1)][95.7%][r=0KiB/s,w=88.9MiB/s][r=0,w=22.8k IOPS][eta 00m:02sJobs: 1 (f=1): [W(1)][97.9%][r=0KiB/s,w=76.7MiB/s][r=0,w=19.6k IOPS][eta 00m:01sJobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=79.8MiB/s][r=0,w=20.4k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14973: Mon Nov 27 15:27:27 2017
  write: IOPS=22.1k, BW=86.4MiB/s (90.6MB/s)(4096MiB/47389msec)
    slat (usec): min=2, max=1153, avg= 6.93, stdev= 4.37
    clat (usec): min=10, max=5101, avg=172.67, stdev=90.36
     lat (usec): min=56, max=5107, avg=179.82, stdev=90.54
    clat percentiles (usec):
     |  1.00th=[   59],  5.00th=[   62], 10.00th=[   69], 20.00th=[   82],
     | 30.00th=[  115], 40.00th=[  159], 50.00th=[  172], 60.00th=[  186],
     | 70.00th=[  204], 80.00th=[  231], 90.00th=[  281], 95.00th=[  326],
     | 99.00th=[  408], 99.50th=[  441], 99.90th=[  660], 99.95th=[ 1074],
     | 99.99th=[ 1647]
   bw (  KiB/s): min=78048, max=99072, per=99.93%, avg=88443.01, stdev=5751.18, samples=94
   iops        : min=19512, max=24768, avg=22110.74, stdev=1437.79, samples=94
  lat (usec)   : 20=0.01%, 50=0.01%, 100=27.48%, 250=57.19%, 500=15.09%
  lat (usec)   : 750=0.14%, 1000=0.02%
  lat (msec)   : 2=0.06%, 4=0.01%, 10=0.01%
  cpu          : usr=2.79%, sys=17.79%, ctx=1048173, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=86.4MiB/s (90.6MB/s), 86.4MiB/s-86.4MiB/s (90.6MB/s-90.6MB/s), io=4096MiB (4295MB), run=47389-47389msec

Disk stats (read/write):
  sda: ios=0/1042574, merge=0/87, ticks=0/177864, in_queue=177688, util=99.82%
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 15:27 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=243MiB/s,w=0KiB/s][r=62.1k,w=0 IOPS][eta 00m:00sJobs: 1 (f=1): [R(1)][100.0%][r=191MiB/s,w=0KiB/s][r=48.8k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=14977: Mon Nov 27 15:28:26 2017
   read: IOPS=58.3k, BW=228MiB/s (239MB/s)(4096MiB/17975msec)
    slat (nsec): min=1438, max=165054, avg=3977.55, stdev=2084.77
    clat (usec): min=13, max=5593, avg=63.70, stdev=40.51
     lat (usec): min=36, max=5596, avg=67.85, stdev=40.51
    clat percentiles (usec):
     |  1.00th=[   40],  5.00th=[   43], 10.00th=[   45], 20.00th=[   47],
     | 30.00th=[   49], 40.00th=[   51], 50.00th=[   53], 60.00th=[   56],
     | 70.00th=[   59], 80.00th=[   67], 90.00th=[   89], 95.00th=[  141],
     | 99.00th=[  241], 99.50th=[  260], 99.90th=[  293], 99.95th=[  314],
     | 99.99th=[ 1004]
   bw (  KiB/s): min=193400, max=252856, per=100.00%, avg=234538.49, stdev=12976.83, samples=35
   iops        : min=48350, max=63214, avg=58634.60, stdev=3244.22, samples=35
  lat (usec)   : 20=0.01%, 50=35.01%, 100=57.27%, 250=6.98%, 500=0.71%
  lat (usec)   : 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=7.37%, sys=32.91%, ctx=748479, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=228MiB/s (239MB/s), 228MiB/s-228MiB/s (239MB/s-239MB/s), io=4096MiB (4295MB), run=17975-17975msec

Disk stats (read/write):
  sda: ios=1044432/2, merge=0/1, ticks=65076/0, in_queue=64976, util=99.46%
```

## itldc lax - 992M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            479M     0  479M   0% /dev
tmpfs           100M  3.0M   97M   3% /run
/dev/vda2       9.5G  1.7G  7.4G  19% /
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           497M     0  497M   0% /sys/fs/cgroup
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=221MiB/s][r=0,w=56.6k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2139: Mon Nov 27 06:27:05 2017
  write: IOPS=60.5k, BW=236MiB/s (248MB/s)(4096MiB/17337msec)
    slat (usec): min=2, max=1829, avg= 7.76, stdev= 7.37
    clat (nsec): min=1025, max=6836.8k, avg=56675.89, stdev=37668.27
     lat (usec): min=22, max=6841, avg=64.78, stdev=38.80
    clat percentiles (usec):
     |  1.00th=[   25],  5.00th=[   31], 10.00th=[   35], 20.00th=[   39],
     | 30.00th=[   43], 40.00th=[   46], 50.00th=[   50], 60.00th=[   57],
     | 70.00th=[   65], 80.00th=[   71], 90.00th=[   81], 95.00th=[   92],
     | 99.00th=[  145], 99.50th=[  206], 99.90th=[  379], 99.95th=[  515],
     | 99.99th=[ 1352]
   bw (  KiB/s): min=196792, max=298904, per=100.00%, avg=241972.71, stdev=25792.27, samples=34
   iops        : min=49198, max=74726, avg=60493.18, stdev=6448.07, samples=34
  lat (usec)   : 2=0.01%, 20=0.07%, 50=49.58%, 100=46.86%, 250=3.13%
  lat (usec)   : 500=0.31%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.02%, 4=0.01%, 10=0.01%
  cpu          : usr=9.16%, sys=46.42%, ctx=468973, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=236MiB/s (248MB/s), 236MiB/s-236MiB/s (248MB/s-248MB/s), io=4096MiB (4295MB), run=17337-17337msec

Disk stats (read/write):
  vda: ios=3/1037064, merge=0/45, ticks=4/42372, in_queue=44480, util=91.31%
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 06:27 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=381MiB/s,w=0KiB/s][r=97.5k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2147: Mon Nov 27 06:28:24 2017
   read: IOPS=90.2k, BW=352MiB/s (369MB/s)(4096MiB/11628msec)
    slat (nsec): min=1217, max=1946.5k, avg=3490.85, stdev=3978.79
    clat (nsec): min=831, max=9813.3k, avg=39738.82, stdev=30996.02
     lat (usec): min=16, max=9821, avg=43.47, stdev=31.47
    clat percentiles (usec):
     |  1.00th=[   20],  5.00th=[   24], 10.00th=[   25], 20.00th=[   28],
     | 30.00th=[   30], 40.00th=[   32], 50.00th=[   36], 60.00th=[   40],
     | 70.00th=[   45], 80.00th=[   50], 90.00th=[   57], 95.00th=[   66],
     | 99.00th=[   99], 99.50th=[  124], 99.90th=[  247], 99.95th=[  330],
     | 99.99th=[ 1106]
   bw (  KiB/s): min=285784, max=421376, per=99.86%, avg=360193.22, stdev=31104.35, samples=23
   iops        : min=71446, max=105344, avg=90048.30, stdev=7776.09, samples=23
  lat (nsec)   : 1000=0.01%
  lat (usec)   : 2=0.01%, 10=0.01%, 20=1.13%, 50=79.55%, 100=18.37%
  lat (usec)   : 250=0.85%, 500=0.07%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=10.73%, sys=45.17%, ctx=281992, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=352MiB/s (369MB/s), 352MiB/s-352MiB/s (369MB/s-369MB/s), io=4096MiB (4295MB), run=11628-11628msec

Disk stats (read/write):
  vda: ios=1024343/2, merge=0/1, ticks=29236/8, in_queue=29152, util=82.79%
```

## impactvps ovz - 1024M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/simfs       15G  1.1G   14G   7% /
devtmpfs        512M     0  512M   0% /dev
tmpfs           512M     0  512M   0% /dev/shm
tmpfs           512M  6.7M  506M   2% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           512M     0  512M   0% /sys/fs/cgroup
tmpfs           103M     0  103M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][16.7%][r=0KiB/s,w=64.5MiB/s][r=0,w=16.5k IOPS][eta 00m:15sJobs: 1 (f=1): [W(1)][18.2%][r=0KiB/s,w=59.9MiB/s][r=0,w=15.3k IOPS][eta 00m:18sJobs: 1 (f=1): [W(1)][20.8%][r=0KiB/s,w=96.7MiB/s][r=0,w=24.8k IOPS][eta 00m:19sJobs: 1 (f=1): [W(1)][22.2%][r=0KiB/s,w=54.9MiB/s][r=0,w=14.0k IOPS][eta 00m:21sJobs: 1 (f=1): [W(1)][21.9%][r=0KiB/s,w=5464KiB/s][r=0,w=1366 IOPS][eta 00m:25s]Jobs: 1 (f=1): [W(1)][28.6%][r=0KiB/s,w=67.3MiB/s][r=0,w=17.2k IOPS][eta 00m:25sJobs: 1 (f=1): [W(1)][31.4%][r=0KiB/s,w=107MiB/s][r=0,w=27.3k IOPS][eta 00m:24s]Jobs: 1 (f=1): [W(1)][32.5%][r=0KiB/s,w=55.5MiB/s][r=0,w=14.2k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][34.1%][r=0KiB/s,w=48.0MiB/s][r=0,w=12.3k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][34.9%][r=0KiB/s,w=43.1MiB/s][r=0,w=11.0k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][36.4%][r=0KiB/s,w=50.8MiB/s][r=0,w=13.0k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][37.8%][r=0KiB/s,w=60.2MiB/s][r=0,w=15.4k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][39.1%][r=0KiB/s,w=68.1MiB/s][r=0,w=17.4k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][40.4%][r=0KiB/s,w=64.5MiB/s][r=0,w=16.5k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][40.8%][r=0KiB/s,w=14.8MiB/s][r=0,w=3781 IOPS][eta 00m:29s]Jobs: 1 (f=1): [W(1)][43.1%][r=0KiB/s,w=61.2MiB/s][r=0,w=15.7k IOPS][eta 00m:29sJobs: 1 (f=1): [W(1)][43.4%][r=0KiB/s,w=6918KiB/s][r=0,w=1729 IOPS][eta 00m:30s]Jobs: 1 (f=1): [W(1)][50.9%][r=0KiB/s,w=77.6MiB/s][r=0,w=19.9k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][51.8%][r=0KiB/s,w=27.5MiB/s][r=0,w=7036 IOPS][eta 00m:27s]Jobs: 1 (f=1): [W(1)][64.9%][r=0KiB/s,w=73.9MiB/s][r=0,w=18.9k IOPS][eta 00m:20sJobs: 1 (f=1): [W(1)][67.9%][r=0KiB/s,w=95.3MiB/s][r=0,w=24.4k IOPS][eta 00m:18sJobs: 1 (f=1): [W(1)][68.4%][r=0KiB/s,w=22.6MiB/s][r=0,w=5789 IOPS][eta 00m:18s]Jobs: 1 (f=1): [W(1)][77.8%][r=0KiB/s,w=96.3MiB/s][r=0,w=24.6k IOPS][eta 00m:12sJobs: 1 (f=1): [W(1)][78.2%][r=0KiB/s,w=10.6MiB/s][r=0,w=2726 IOPS][eta 00m:12s]Jobs: 1 (f=1): [W(1)][85.2%][r=0KiB/s,w=88.7MiB/s][r=0,w=22.7k IOPS][eta 00m:08sJobs: 1 (f=1): [W(1)][87.0%][r=0KiB/s,w=35.0MiB/s][r=0,w=9211 IOPS][eta 00m:07s]Jobs: 1 (f=1): [W(1)][88.9%][r=0KiB/s,w=95.5MiB/s][r=0,w=24.4k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][90.7%][r=0KiB/s,w=52.2MiB/s][r=0,w=13.4k IOPS][eta 00m:05sJobs: 1 (f=1): [W(1)][90.9%][r=0KiB/s,w=32.0MiB/s][r=0,w=8201 IOPS][eta 00m:05s]Jobs: 1 (f=1): [W(1)][92.7%][r=0KiB/s,w=87.8MiB/s][r=0,w=22.5k IOPS][eta 00m:04sJobs: 1 (f=1): [W(1)][94.5%][r=0KiB/s,w=32.1MiB/s][r=0,w=8225 IOPS][eta 00m:03s]Jobs: 1 (f=1): [W(1)][94.6%][r=0KiB/s,w=51.2MiB/s][r=0,w=13.1k IOPS][eta 00m:03sJobs: 1 (f=1): [W(1)][96.4%][r=0KiB/s,w=24.8MiB/s][r=0,w=6357 IOPS][eta 00m:02s]Jobs: 1 (f=1): [W(1)][96.5%][r=0KiB/s,w=10.7MiB/s][r=0,w=2743 IOPS][eta 00m:02s]
myjob: (groupid=0, jobs=1): err= 0: pid=27862: Mon Nov 27 15:02:04 2017
  write: IOPS=18.8k, BW=73.6MiB/s (77.2MB/s)(4096MiB/55633msec)
    slat (usec): min=2, max=1173.4k, avg=52.32, stdev=4035.58
    clat (nsec): min=1094, max=1173.5M, avg=159455.98, stdev=7081353.38
     lat (usec): min=4, max=1173.5k, avg=211.83, stdev=8190.53
    clat percentiles (usec):
     |  1.00th=[    13],  5.00th=[    13], 10.00th=[    13], 20.00th=[    13],
     | 30.00th=[    13], 40.00th=[    14], 50.00th=[    14], 60.00th=[    15],
     | 70.00th=[    16], 80.00th=[    18], 90.00th=[    21], 95.00th=[    28],
     | 99.00th=[   392], 99.50th=[   441], 99.90th=[  5407], 99.95th=[ 50594],
     | 99.99th=[459277]
   bw (  KiB/s): min=  344, max=762120, per=100.00%, avg=78174.34, stdev=112692.64, samples=106
   iops        : min=   86, max=190530, avg=19543.56, stdev=28173.17, samples=106
  lat (usec)   : 2=0.01%, 10=0.01%, 20=88.61%, 50=8.04%, 100=0.11%
  lat (usec)   : 250=0.06%, 500=2.76%, 750=0.20%, 1000=0.03%
  lat (msec)   : 2=0.05%, 4=0.02%, 10=0.02%, 20=0.01%, 50=0.03%
  lat (msec)   : 100=0.02%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2000=0.01%
  cpu          : usr=1.30%, sys=15.49%, ctx=12922, majf=0, minf=50
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=73.6MiB/s (77.2MB/s), 73.6MiB/s-73.6MiB/s (77.2MB/s-77.2MB/s), io=4096MiB (4295MB), run=55633-55633msec
```

*file-size*
```
ls -al test4K-aio 
-rw-r--r-- 1 deploy deploy 4294967296 Nov 27 15:02 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=311MiB/s,w=0KiB/s][r=79.6k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=27893: Mon Nov 27 15:03:05 2017
   read: IOPS=70.1k, BW=274MiB/s (287MB/s)(4096MiB/14965msec)
    slat (nsec): min=1045, max=78176k, avg=11029.27, stdev=205315.74
    clat (nsec): min=977, max=78209k, avg=35511.27, stdev=355345.06
     lat (usec): min=2, max=78213, avg=46.60, stdev=410.04
    clat percentiles (usec):
     |  1.00th=[    6],  5.00th=[    6], 10.00th=[    6], 20.00th=[    6],
     | 30.00th=[    6], 40.00th=[    6], 50.00th=[    6], 60.00th=[    6],
     | 70.00th=[    7], 80.00th=[    9], 90.00th=[   10], 95.00th=[   38],
     | 99.00th=[  611], 99.50th=[  816], 99.90th=[ 5014], 99.95th=[ 6521],
     | 99.99th=[ 9634]
   bw (  KiB/s): min=217088, max=471632, per=100.00%, avg=335810.58, stdev=64581.30, samples=24
   iops        : min=54272, max=117908, avg=83952.58, stdev=16145.32, samples=24
  lat (nsec)   : 1000=0.01%
  lat (usec)   : 4=0.01%, 10=92.29%, 20=2.43%, 50=0.32%, 100=0.93%
  lat (usec)   : 250=0.30%, 500=2.27%, 750=0.86%, 1000=0.30%
  lat (msec)   : 2=0.17%, 4=0.01%, 10=0.10%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%
  cpu          : usr=4.30%, sys=48.63%, ctx=17002, majf=0, minf=43
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=274MiB/s (287MB/s), 274MiB/s-274MiB/s (287MB/s-287MB/s), io=4096MiB (4295MB), run=14965-14965msec
```

## launchvps lax - 2000M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            981M     0  981M   0% /dev
tmpfs           201M  3.1M  197M   2% /run
/dev/vda1        28G  1.9G   25G   8% /
tmpfs          1001M     0 1001M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs          1001M     0 1001M   0% /sys/fs/cgroup
tmpfs           201M     0  201M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][54.2%][r=0KiB/s,w=83.5MiB/s][r=0,w=21.4k IOPS][eta 00m:11sJobs: 1 (f=1): [W(1)][58.3%][r=0KiB/s,w=219MiB/s][r=0,w=56.1k IOPS][eta 00m:10s]Jobs: 1 (f=1): [W(1)][63.0%][r=0KiB/s,w=55.6MiB/s][r=0,w=14.2k IOPS][eta 00m:10sJobs: 1 (f=1): [W(1)][69.2%][r=0KiB/s,w=207MiB/s][r=0,w=53.1k IOPS][eta 00m:08s]Jobs: 1 (f=1): [W(1)][78.6%][r=0KiB/s,w=64.3MiB/s][r=0,w=16.5k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][82.1%][r=0KiB/s,w=186MiB/s][r=0,w=47.7k IOPS][eta 00m:05s]Jobs: 1 (f=1): [W(1)][93.3%][r=0KiB/s,w=75.3MiB/s][r=0,w=19.3k IOPS][eta 00m:02sJobs: 1 (f=1): [W(1)][96.6%][r=0KiB/s,w=195MiB/s][r=0,w=49.8k IOPS][eta 00m:01s]Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=130MiB/s][r=0,w=33.2k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=6951: Tue Nov 28 09:33:05 2017
  write: IOPS=35.7k, BW=139MiB/s (146MB/s)(4096MiB/29392msec)
    slat (usec): min=2, max=50941, avg= 6.35, stdev=96.47
    clat (nsec): min=673, max=1639.0M, avg=104592.41, stdev=4664265.45
     lat (usec): min=17, max=1639.0k, avg=111.16, stdev=4665.94
    clat percentiles (usec):
     |  1.00th=[   25],  5.00th=[   31], 10.00th=[   34], 20.00th=[   39],
     | 30.00th=[   42], 40.00th=[   45], 50.00th=[   48], 60.00th=[   52],
     | 70.00th=[   59], 80.00th=[   70], 90.00th=[   93], 95.00th=[  137],
     | 99.00th=[  330], 99.50th=[  611], 99.90th=[ 8455], 99.95th=[14615],
     | 99.99th=[43254]
   bw (  KiB/s): min= 1424, max=300912, per=100.00%, avg=152867.19, stdev=68068.37, samples=54
   iops        : min=  356, max=75228, avg=38216.70, stdev=17017.13, samples=54
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 10=0.01%, 20=0.14%, 50=55.89%, 100=35.32%
  lat (usec)   : 250=7.08%, 500=0.98%, 750=0.16%, 1000=0.08%
  lat (msec)   : 2=0.11%, 4=0.06%, 10=0.09%, 20=0.05%, 50=0.03%
  lat (msec)   : 100=0.01%, 250=0.01%, 2000=0.01%
  cpu          : usr=7.35%, sys=34.23%, ctx=269781, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=139MiB/s (146MB/s), 139MiB/s-139MiB/s (146MB/s-146MB/s), io=4096MiB (4295MB), run=29392-29392msec

Disk stats (read/write):
  vda: ios=0/1036729, merge=0/49, ticks=0/81544, in_queue=81468, util=78.97%
```

*file-size*
```
ls -al test4K-aio
-rw-r--r-- 1 deploy deploy 4294967296 Nov 28 09:33 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][11.1%][r=79.1MiB/s,w=0KiB/s][r=20.3k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [R(1)][13.2%][r=84.8MiB/s,w=0KiB/s][r=21.7k,w=0 IOPS][eta 00m:46sJobs: 1 (f=1): [R(1)][15.1%][r=78.9MiB/s,w=0KiB/s][r=20.2k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [R(1)][18.5%][r=75.8MiB/s,w=0KiB/s][r=19.4k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [R(1)][19.2%][r=86.9MiB/s,w=0KiB/s][r=22.2k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [R(1)][20.8%][r=71.6MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [R(1)][22.6%][r=74.2MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][25.0%][r=87.3MiB/s,w=0KiB/s][r=22.4k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [R(1)][26.9%][r=74.4MiB/s,w=0KiB/s][r=19.1k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [R(1)][28.8%][r=77.8MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [R(1)][30.8%][r=94.5MiB/s,w=0KiB/s][r=24.2k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][32.7%][r=76.1MiB/s,w=0KiB/s][r=19.5k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [R(1)][34.6%][r=75.2MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][37.3%][r=96.7MiB/s,w=0KiB/s][r=24.8k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][39.2%][r=79.0MiB/s,w=0KiB/s][r=20.2k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][41.2%][r=74.8MiB/s,w=0KiB/s][r=19.1k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][43.1%][r=77.5MiB/s,w=0KiB/s][r=19.8k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][44.2%][r=75.5MiB/s,w=0KiB/s][r=19.3k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][46.2%][r=75.5MiB/s,w=0KiB/s][r=19.3k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [R(1)][49.0%][r=95.3MiB/s,w=0KiB/s][r=24.4k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][51.0%][r=77.5MiB/s,w=0KiB/s][r=19.8k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [R(1)][52.9%][r=76.9MiB/s,w=0KiB/s][r=19.7k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [R(1)][54.9%][r=93.4MiB/s,w=0KiB/s][r=23.9k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][56.9%][r=74.5MiB/s,w=0KiB/s][r=19.1k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [R(1)][58.8%][r=76.4MiB/s,w=0KiB/s][r=19.6k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][60.8%][r=84.5MiB/s,w=0KiB/s][r=21.6k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [R(1)][62.7%][r=75.9MiB/s,w=0KiB/s][r=19.4k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [R(1)][64.7%][r=71.1MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][66.7%][r=89.3MiB/s,w=0KiB/s][r=22.9k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][68.6%][r=75.7MiB/s,w=0KiB/s][r=19.4k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [R(1)][73.5%][r=186MiB/s,w=0KiB/s][r=47.6k,w=0 IOPS][eta 00m:13s]Jobs: 1 (f=1): [R(1)][92.7%][r=390MiB/s,w=0KiB/s][r=99.0k,w=0 IOPS][eta 00m:03s]
myjob: (groupid=0, jobs=1): err= 0: pid=6959: Tue Nov 28 09:34:46 2017
   read: IOPS=27.1k, BW=106MiB/s (111MB/s)(4096MiB/38705msec)
    slat (nsec): min=1097, max=2271.6k, avg=3831.38, stdev=4328.16
    clat (usec): min=4, max=32225, avg=142.81, stdev=185.35
     lat (usec): min=12, max=32229, avg=146.82, stdev=185.46
    clat percentiles (usec):
     |  1.00th=[   21],  5.00th=[   25], 10.00th=[   29], 20.00th=[   35],
     | 30.00th=[   43], 40.00th=[   67], 50.00th=[  133], 60.00th=[  184],
     | 70.00th=[  206], 80.00th=[  221], 90.00th=[  245], 95.00th=[  289],
     | 99.00th=[  537], 99.50th=[  758], 99.90th=[ 2114], 99.95th=[ 2704],
     | 99.99th=[ 4424]
   bw (  KiB/s): min=68976, max=442424, per=98.45%, avg=106681.97, stdev=88286.93, samples=77
   iops        : min=17244, max=110606, avg=26670.49, stdev=22071.73, samples=77
  lat (usec)   : 10=0.01%, 20=0.81%, 50=33.47%, 100=10.18%, 250=46.84%
  lat (usec)   : 500=7.55%, 750=0.64%, 1000=0.19%
  lat (msec)   : 2=0.21%, 4=0.09%, 10=0.02%, 20=0.01%, 50=0.01%
  cpu          : usr=5.29%, sys=19.32%, ctx=338393, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=106MiB/s (111MB/s), 106MiB/s-106MiB/s (111MB/s-111MB/s), io=4096MiB (4295MB), run=38705-38705msec

Disk stats (read/write):
  vda: ios=1042737/4, merge=0/2, ticks=131308/0, in_queue=131212, util=92.27%
```

## serverhand lax - 2000M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            982M     0  982M   0% /dev
tmpfs           201M  3.2M  197M   2% /run
/dev/sda1        49G  1.8G   44G   4% /
tmpfs          1001M     0 1001M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs          1001M     0 1001M   0% /sys/fs/cgroup
tmpfs           201M     0  201M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=16.0MiB/s][r=0,w=4105 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16597: Wed Nov 29 14:06:04 2017
  write: IOPS=3935, BW=15.4MiB/s (16.1MB/s)(4096MiB/266439msec)
    slat (nsec): min=1984, max=1397.9k, avg=6550.65, stdev=4269.83
    clat (usec): min=273, max=439818, avg=1007.80, stdev=964.26
     lat (usec): min=356, max=439825, avg=1014.58, stdev=964.47
    clat percentiles (usec):
     |  1.00th=[  799],  5.00th=[  824], 10.00th=[  840], 20.00th=[  857],
     | 30.00th=[  873], 40.00th=[  889], 50.00th=[  914], 60.00th=[  947],
     | 70.00th=[  996], 80.00th=[ 1057], 90.00th=[ 1172], 95.00th=[ 1303],
     | 99.00th=[ 1582], 99.50th=[ 6128], 99.90th=[ 6652], 99.95th=[ 6783],
     | 99.99th=[ 7046]
   bw (  KiB/s): min= 4328, max=18160, per=99.98%, avg=15739.15, stdev=1470.98, samples=532
   iops        : min= 1082, max= 4540, avg=3934.77, stdev=367.74, samples=532
  lat (usec)   : 500=0.01%, 750=0.03%, 1000=71.08%
  lat (msec)   : 2=28.09%, 4=0.01%, 10=0.78%, 250=0.01%, 500=0.01%
  cpu          : usr=1.25%, sys=3.30%, ctx=1048682, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=15.4MiB/s (16.1MB/s), 15.4MiB/s-15.4MiB/s (16.1MB/s-16.1MB/s), io=4096MiB (4295MB), run=266439-266439msec

Disk stats (read/write):
  sda: ios=0/786204, merge=0/262425, ticks=0/698624, in_queue=698452, util=100.00%
```

*file-size*
```
ls -al test4K-aio
-rw-r--r-- 1 deploy deploy 4294967296 Nov 29 14:06 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=35.6MiB/s,w=0KiB/s][r=9124,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16616: Wed Nov 29 14:11:41 2017
   read: IOPS=8876, BW=34.7MiB/s (36.4MB/s)(4096MiB/118131msec)
    slat (nsec): min=852, max=304340, avg=2756.84, stdev=1132.27
    clat (usec): min=135, max=17466, avg=446.71, stdev=67.70
     lat (usec): min=186, max=17468, avg=449.63, stdev=67.75
    clat percentiles (usec):
     |  1.00th=[  388],  5.00th=[  392], 10.00th=[  396], 20.00th=[  404],
     | 30.00th=[  412], 40.00th=[  420], 50.00th=[  433], 60.00th=[  445],
     | 70.00th=[  465], 80.00th=[  494], 90.00th=[  519], 95.00th=[  537],
     | 99.00th=[  578], 99.50th=[  603], 99.90th=[  701], 99.95th=[  766],
     | 99.99th=[ 1123]
   bw (  KiB/s): min=29584, max=38016, per=99.99%, avg=35502.21, stdev=1266.34, samples=236
   iops        : min= 7396, max= 9504, avg=8875.53, stdev=316.59, samples=236
  lat (usec)   : 250=0.01%, 500=82.30%, 750=17.64%, 1000=0.04%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%
  cpu          : usr=13.78%, sys=44.41%, ctx=786456, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=34.7MiB/s (36.4MB/s), 34.7MiB/s-34.7MiB/s (36.4MB/s-36.4MB/s), io=4096MiB (4295MB), run=118131-118131msec

Disk stats (read/write):
  sda: ios=784828/11, merge=261632/2, ticks=284904/0, in_queue=284768, util=99.97%
```

## hiformance lax - 2000M (/usr/bin/python missing, install via: apt-get install python)
`df -h`
```
Filesystem      Size  Used Avail Use% Mounted on
udev            981M     0  981M   0% /dev
tmpfs           201M  5.8M  195M   3% /run
/dev/vda1        33G  2.5G   30G   8% /
tmpfs          1001M     0 1001M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs          1001M     0 1001M   0% /sys/fs/cgroup
tmpfs           201M     0  201M   0% /run/user/901
```

*writes*
```
./fio --filename=test4K-aio --rw=write --ioengine=libaio --direct=1 --blocksize=4K --size=4G --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][11.9%][r=0KiB/s,w=92.3MiB/s][r=0,w=23.6k IOPS][eta 00m:37sJobs: 1 (f=1): [W(1)][14.0%][r=0KiB/s,w=92.2MiB/s][r=0,w=23.6k IOPS][eta 00m:37sJobs: 1 (f=1): [W(1)][16.3%][r=0KiB/s,w=95.4MiB/s][r=0,w=24.4k IOPS][eta 00m:36sJobs: 1 (f=1): [W(1)][18.6%][r=0KiB/s,w=97.3MiB/s][r=0,w=24.9k IOPS][eta 00m:35sJobs: 1 (f=1): [W(1)][21.4%][r=0KiB/s,w=100MiB/s][r=0,w=25.6k IOPS][eta 00m:33s]Jobs: 1 (f=1): [W(1)][31.7%][r=0KiB/s,w=93.6MiB/s][r=0,w=23.0k IOPS][eta 00m:28sJobs: 1 (f=1): [W(1)][34.1%][r=0KiB/s,w=89.7MiB/s][r=0,w=22.0k IOPS][eta 00m:27sJobs: 1 (f=1): [W(1)][36.6%][r=0KiB/s,w=97.2MiB/s][r=0,w=24.9k IOPS][eta 00m:26sJobs: 1 (f=1): [W(1)][39.0%][r=0KiB/s,w=101MiB/s][r=0,w=25.9k IOPS][eta 00m:25s]Jobs: 1 (f=1): [W(1)][48.8%][r=0KiB/s,w=89.5MiB/s][r=0,w=22.9k IOPS][eta 00m:21sJobs: 1 (f=1): [W(1)][51.2%][r=0KiB/s,w=87.3MiB/s][r=0,w=22.3k IOPS][eta 00m:20sJobs: 1 (f=1): [W(1)][53.7%][r=0KiB/s,w=92.5MiB/s][r=0,w=23.7k IOPS][eta 00m:19sJobs: 1 (f=1): [W(1)][56.1%][r=0KiB/s,w=97.1MiB/s][r=0,w=24.9k IOPS][eta 00m:18sJobs: 1 (f=1): [W(1)][58.5%][r=0KiB/s,w=95.1MiB/s][r=0,w=24.3k IOPS][eta 00m:17sJobs: 1 (f=1): [W(1)][61.0%][r=0KiB/s,w=97.6MiB/s][r=0,w=24.0k IOPS][eta 00m:16sJobs: 1 (f=1): [W(1)][63.4%][r=0KiB/s,w=94.7MiB/s][r=0,w=24.2k IOPS][eta 00m:15sJobs: 1 (f=1): [W(1)][64.3%][r=0KiB/s,w=90.8MiB/s][r=0,w=23.2k IOPS][eta 00m:15sJobs: 1 (f=1): [W(1)][66.7%][r=0KiB/s,w=94.6MiB/s][r=0,w=24.2k IOPS][eta 00m:14sJobs: 1 (f=1): [W(1)][69.0%][r=0KiB/s,w=92.9MiB/s][r=0,w=23.8k IOPS][eta 00m:13sJobs: 1 (f=1): [W(1)][71.4%][r=0KiB/s,w=103MiB/s][r=0,w=26.5k IOPS][eta 00m:12s]Jobs: 1 (f=1): [W(1)][80.5%][r=0KiB/s,w=91.3MiB/s][r=0,w=23.4k IOPS][eta 00m:08sJobs: 1 (f=1): [W(1)][81.0%][r=0KiB/s,w=85.8MiB/s][r=0,w=21.0k IOPS][eta 00m:08sJobs: 1 (f=1): [W(1)][83.3%][r=0KiB/s,w=102MiB/s][r=0,w=25.0k IOPS][eta 00m:07s]Jobs: 1 (f=1): [W(1)][85.7%][r=0KiB/s,w=90.7MiB/s][r=0,w=23.2k IOPS][eta 00m:06sJobs: 1 (f=1): [W(1)][88.1%][r=0KiB/s,w=96.0MiB/s][r=0,w=24.8k IOPS][eta 00m:05sJobs: 1 (f=1): [W(1)][90.5%][r=0KiB/s,w=96.3MiB/s][r=0,w=24.7k IOPS][eta 00m:04sJobs: 1 (f=1): [W(1)][92.9%][r=0KiB/s,w=97.6MiB/s][r=0,w=24.0k IOPS][eta 00m:03sJobs: 1 (f=1): [W(1)][95.2%][r=0KiB/s,w=94.1MiB/s][r=0,w=24.1k IOPS][eta 00m:02sJobs: 1 (f=1): [W(1)][97.6%][r=0KiB/s,w=96.6MiB/s][r=0,w=24.7k IOPS][eta 00m:01sJobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=91.8MiB/s][r=0,w=23.5k IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2282: Sat Dec  2 05:25:42 2017
  write: IOPS=24.9k, BW=97.1MiB/s (102MB/s)(4096MiB/42172msec)
    slat (usec): min=2, max=1051, avg= 9.37, stdev= 6.66
    clat (usec): min=20, max=18845, avg=149.38, stdev=157.35
     lat (usec): min=70, max=18852, avg=159.08, stdev=157.44
    clat percentiles (usec):
     |  1.00th=[   82],  5.00th=[   92], 10.00th=[   99], 20.00th=[  110],
     | 30.00th=[  117], 40.00th=[  124], 50.00th=[  130], 60.00th=[  139],
     | 70.00th=[  147], 80.00th=[  161], 90.00th=[  192], 95.00th=[  243],
     | 99.00th=[  537], 99.50th=[  660], 99.90th=[ 1352], 99.95th=[ 2278],
     | 99.99th=[ 6849]
   bw (  KiB/s): min=80608, max=114536, per=100.00%, avg=99491.36, stdev=7177.00, samples=84
   iops        : min=20152, max=28634, avg=24872.86, stdev=1794.24, samples=84
  lat (usec)   : 50=0.01%, 100=10.85%, 250=84.47%, 500=3.49%, 750=0.87%
  lat (usec)   : 1000=0.12%
  lat (msec)   : 2=0.13%, 4=0.04%, 10=0.02%, 20=0.01%
  cpu          : usr=6.25%, sys=24.23%, ctx=550151, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
  WRITE: bw=97.1MiB/s (102MB/s), 97.1MiB/s-97.1MiB/s (102MB/s-102MB/s), io=4096MiB (4295MB), run=42172-42172msec

Disk stats (read/write):
  vda: ios=0/1047807, merge=0/86, ticks=0/131928, in_queue=131708, util=94.05%
```

*file-size*
```
ls -al test4K-aio
-rw-r--r-- 1 deploy deploy 4294967296 Dec  2 05:25 test4K-aio
```

*reads*
```
./fio --filename=test4K-aio --rw=read --ioengine=libaio --direct=1 --blocksize=4K --runtime=300 --iodepth=4 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=4
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][10.9%][r=96.9MiB/s,w=0KiB/s][r=24.8k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][10.9%][r=86.7MiB/s,w=0KiB/s][r=22.2k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [R(1)][13.0%][r=79.9MiB/s,w=0KiB/s][r=20.4k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [R(1)][14.9%][r=83.9MiB/s,w=0KiB/s][r=21.5k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [R(1)][18.4%][r=74.9MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [R(1)][18.8%][r=75.2MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [R(1)][20.4%][r=78.7MiB/s,w=0KiB/s][r=20.1k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [R(1)][22.4%][r=77.9MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [R(1)][24.5%][r=80.0MiB/s,w=0KiB/s][r=20.7k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [R(1)][26.5%][r=77.7MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][28.0%][r=71.3MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [R(1)][30.0%][r=67.5MiB/s,w=0KiB/s][r=17.3k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [R(1)][32.0%][r=80.5MiB/s,w=0KiB/s][r=20.6k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [R(1)][34.0%][r=78.0MiB/s,w=0KiB/s][r=20.2k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [R(1)][36.0%][r=79.2MiB/s,w=0KiB/s][r=20.3k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [R(1)][38.0%][r=84.7MiB/s,w=0KiB/s][r=21.7k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [R(1)][40.0%][r=89.2MiB/s,w=0KiB/s][r=22.8k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [R(1)][42.0%][r=78.4MiB/s,w=0KiB/s][r=20.1k,w=0 IOPS][eta 00m:29sJobs: 1 (f=1): [R(1)][44.0%][r=77.2MiB/s,w=0KiB/s][r=19.8k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [R(1)][46.0%][r=76.7MiB/s,w=0KiB/s][r=19.6k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][47.1%][r=61.3MiB/s,w=0KiB/s][r=15.7k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [R(1)][49.0%][r=71.9MiB/s,w=0KiB/s][r=18.4k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [R(1)][51.0%][r=87.7MiB/s,w=0KiB/s][r=22.4k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [R(1)][52.9%][r=87.4MiB/s,w=0KiB/s][r=22.4k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [R(1)][54.9%][r=83.6MiB/s,w=0KiB/s][r=21.4k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [R(1)][58.0%][r=83.5MiB/s,w=0KiB/s][r=21.4k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][58.8%][r=76.6MiB/s,w=0KiB/s][r=19.6k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [R(1)][62.0%][r=84.6MiB/s,w=0KiB/s][r=21.7k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [R(1)][64.0%][r=94.3MiB/s,w=0KiB/s][r=24.2k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [R(1)][66.0%][r=95.7MiB/s,w=0KiB/s][r=24.5k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [R(1)][68.0%][r=93.1MiB/s,w=0KiB/s][r=23.8k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [R(1)][70.0%][r=84.0MiB/s,w=0KiB/s][r=21.5k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [R(1)][72.0%][r=77.0MiB/s,w=0KiB/s][r=19.7k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [R(1)][74.0%][r=92.8MiB/s,w=0KiB/s][r=23.8k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [R(1)][77.6%][r=88.6MiB/s,w=0KiB/s][r=22.7k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [R(1)][79.6%][r=90.2MiB/s,w=0KiB/s][r=23.1k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [R(1)][82.0%][r=84.9MiB/s,w=0KiB/s][r=21.7k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [R(1)][83.7%][r=88.5MiB/s,w=0KiB/s][r=22.7k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [R(1)][85.7%][r=88.3MiB/s,w=0KiB/s][r=22.6k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [R(1)][87.8%][r=80.0MiB/s,w=0KiB/s][r=20.7k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [R(1)][89.8%][r=80.8MiB/s,w=0KiB/s][r=20.7k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [R(1)][91.8%][r=84.0MiB/s,w=0KiB/s][r=21.5k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [R(1)][93.9%][r=85.8MiB/s,w=0KiB/s][r=21.0k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [R(1)][95.9%][r=80.5MiB/s,w=0KiB/s][r=20.6k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [R(1)][98.0%][r=82.0MiB/s,w=0KiB/s][r=21.2k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [R(1)][100.0%][r=88.2MiB/s,w=0KiB/s][r=22.6k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=2292: Sat Dec  2 05:27:19 2017
   read: IOPS=21.2k, BW=82.8MiB/s (86.9MB/s)(4096MiB/49452msec)
    slat (nsec): min=1473, max=4348.2k, avg=7584.43, stdev=7361.97
    clat (usec): min=11, max=18947, avg=178.90, stdev=341.75
     lat (usec): min=15, max=18950, avg=186.77, stdev=341.88
    clat percentiles (usec):
     |  1.00th=[   71],  5.00th=[   85], 10.00th=[   93], 20.00th=[  103],
     | 30.00th=[  113], 40.00th=[  121], 50.00th=[  129], 60.00th=[  141],
     | 70.00th=[  155], 80.00th=[  178], 90.00th=[  235], 95.00th=[  351],
     | 99.00th=[  955], 99.50th=[ 2024], 99.90th=[ 4948], 99.95th=[ 7046],
     | 99.99th=[10945]
   bw (  KiB/s): min=59936, max=109184, per=99.99%, avg=84803.17, stdev=8452.49, samples=98
   iops        : min=14984, max=27296, avg=21200.78, stdev=2113.15, samples=98
  lat (usec)   : 20=0.01%, 50=0.32%, 100=16.25%, 250=74.63%, 500=6.07%
  lat (usec)   : 750=1.35%, 1000=0.43%
  lat (msec)   : 2=0.44%, 4=0.32%, 10=0.17%, 20=0.02%
  cpu          : usr=7.87%, sys=20.75%, ctx=435732, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=4

Run status group 0 (all jobs):
   READ: bw=82.8MiB/s (86.9MB/s), 82.8MiB/s-82.8MiB/s (86.9MB/s-86.9MB/s), io=4096MiB (4295MB), run=49452-49452msec

Disk stats (read/write):
  vda: ios=1047506/3, merge=0/1, ticks=170152/0, in_queue=169808, util=96.66%
```

