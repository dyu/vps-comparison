# fio results
```
# random writes
fio --filename=test --rw=write --ioengine=posixaio --direct=1 --blocksize=128K --size=4G --iodepth=32 --group_reporting --name=myjob

# random reads
fio --filename=test --rw=read --ioengine=posixaio --direct=1 --blocksize=128K --runtime=300 --iodepth=32 --group_reporting --name=myjob
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
./fio --filename=test --rw=write --ioengine=posixaio --direct=1 --blocksize=128K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 128KiB-128KiB, (W) 128KiB-128KiB, (T) 128KiB-128KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=60.1MiB/s][r=0,w=480 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18465: Thu Oct  5 15:42:02 2017
  write: IOPS=495, BW=61.9MiB/s (64.0MB/s)(4096MiB/66118msec)
    slat (nsec): min=1811, max=71366, avg=5846.89, stdev=1495.34
    clat (msec): min=35, max=192, avg=64.49, stdev=12.69
     lat (msec): min=35, max=192, avg=64.49, stdev=12.69
    clat percentiles (msec):
     |  1.00th=[   45],  5.00th=[   46], 10.00th=[   47], 20.00th=[   51],
     | 30.00th=[   58], 40.00th=[   61], 50.00th=[   66], 60.00th=[   70],
     | 70.00th=[   73], 80.00th=[   77], 90.00th=[   80], 95.00th=[   82],
     | 99.00th=[   87], 99.50th=[   93], 99.90th=[  122], 99.95th=[  192],
     | 99.99th=[  192]
   bw (  KiB/s): min=49152, max=73728, per=99.96%, avg=63413.12, stdev=4650.14, samples=132
   iops        : min=  384, max=  576, avg=495.35, stdev=36.27, samples=132
  lat (msec)   : 50=18.77%, 100=81.05%, 250=0.18%
  cpu          : usr=0.42%, sys=0.03%, ctx=16392, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,32768,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=61.9MiB/s (64.0MB/s), 61.9MiB/s-61.9MiB/s (64.0MB/s-64.0MB/s), io=4096MiB (4295MB), run=66118-66118msec

Disk stats (read/write):
  xvda: ios=2/32671, merge=0/64, ticks=0/65340, in_queue=65340, util=99.09%
```

*file-size*
```
ls -al test
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 15:42 test
```

*reads*
```
./fio --filename=test --rw=read --ioengine=posixaio --direct=1 --blocksize=128K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 128KiB-128KiB, (W) 128KiB-128KiB, (T) 128KiB-128KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=60.1MiB/s,w=0KiB/s][r=480,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18469: Thu Oct  5 15:44:05 2017
   read: IOPS=495, BW=61.0MiB/s (64.0MB/s)(4096MiB/66113msec)
    slat (nsec): min=185, max=100043, avg=431.61, stdev=687.69
    clat (msec): min=15, max=139, avg=64.54, stdev= 9.38
     lat (msec): min=15, max=139, avg=64.54, stdev= 9.38
    clat percentiles (msec):
     |  1.00th=[   24],  5.00th=[   46], 10.00th=[   61], 20.00th=[   66],
     | 30.00th=[   66], 40.00th=[   66], 50.00th=[   66], 60.00th=[   66],
     | 70.00th=[   66], 80.00th=[   66], 90.00th=[   67], 95.00th=[   74],
     | 99.00th=[   91], 99.50th=[  102], 99.90th=[  129], 99.95th=[  134],
     | 99.99th=[  134]
   bw (  KiB/s): min=57088, max=155648, per=99.96%, avg=63415.85, stdev=9166.58, samples=132
   iops        : min=  446, max= 1216, avg=495.40, stdev=71.61, samples=132
  lat (msec)   : 20=0.64%, 50=5.68%, 100=93.11%, 250=0.57%
  cpu          : usr=0.17%, sys=0.00%, ctx=16388, majf=0, minf=20
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=32768,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=61.0MiB/s (64.0MB/s), 61.0MiB/s-61.0MiB/s (64.0MB/s-64.0MB/s), io=4096MiB (4295MB), run=66113-66113msec

Disk stats (read/write):
  xvda: ios=32663/3, merge=0/1, ticks=65500/0, in_queue=65500, util=99.32%
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
./fio --filename=test --rw=write --ioengine=posixaio --direct=1 --blocksize=128K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 128KiB-128KiB, (W) 128KiB-128KiB, (T) 128KiB-128KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=36.0MiB/s][r=0,w=288 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=32745: Thu Oct  5 15:51:21 2017
  write: IOPS=268, BW=33.6MiB/s (35.2MB/s)(4096MiB/121949msec)
    slat (nsec): min=1854, max=263319, avg=11765.18, stdev=6318.78
    clat (msec): min=55, max=401, avg=118.93, stdev=28.12
     lat (msec): min=55, max=401, avg=118.95, stdev=28.12
    clat percentiles (msec):
     |  1.00th=[   69],  5.00th=[   86], 10.00th=[   95], 20.00th=[  106],
     | 30.00th=[  110], 40.00th=[  112], 50.00th=[  113], 60.00th=[  115],
     | 70.00th=[  120], 80.00th=[  130], 90.00th=[  148], 95.00th=[  171],
     | 99.00th=[  232], 99.50th=[  251], 99.90th=[  338], 99.95th=[  401],
     | 99.99th=[  401]
   bw (  KiB/s): min= 8192, max=41042, per=99.98%, avg=34386.79, stdev=5944.50, samples=243
   iops        : min=   64, max=  320, avg=268.63, stdev=46.44, samples=243
  lat (msec)   : 100=13.65%, 250=85.85%, 500=0.50%
  cpu          : usr=0.51%, sys=0.04%, ctx=16399, majf=0, minf=19
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,32768,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=33.6MiB/s (35.2MB/s), 33.6MiB/s-33.6MiB/s (35.2MB/s-35.2MB/s), io=4096MiB (4295MB), run=121949-121949msec

Disk stats (read/write):
  sda: ios=211/32839, merge=0/140, ticks=1984/117704, in_queue=119620, util=96.40%
```

*file-size*
```
ls -al test 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 15:51 test
```

*reads*
```
./fio --filename=test --rw=read --ioengine=posixaio --direct=1 --blocksize=128K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 128KiB-128KiB, (W) 128KiB-128KiB, (T) 128KiB-128KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=56.1MiB/s,w=0KiB/s][r=448,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=32761: Thu Oct  5 15:53:40 2017
   read: IOPS=459, BW=57.5MiB/s (60.3MB/s)(4096MiB/71243msec)
    slat (nsec): min=104, max=568317, avg=632.68, stdev=3484.29
    clat (msec): min=20, max=259, avg=69.55, stdev=22.71
     lat (msec): min=20, max=259, avg=69.55, stdev=22.71
    clat percentiles (msec):
     |  1.00th=[   32],  5.00th=[   40], 10.00th=[   45], 20.00th=[   52],
     | 30.00th=[   56], 40.00th=[   62], 50.00th=[   67], 60.00th=[   71],
     | 70.00th=[   79], 80.00th=[   87], 90.00th=[  100], 95.00th=[  112],
     | 99.00th=[  138], 99.50th=[  155], 99.90th=[  171], 99.95th=[  226],
     | 99.99th=[  232]
   bw (  KiB/s): min=24064, max=74496, per=100.00%, avg=58900.82, stdev=8283.46, samples=142
   iops        : min=  188, max=  582, avg=460.15, stdev=64.72, samples=142
  lat (msec)   : 50=18.72%, 100=71.75%, 250=9.52%, 500=0.01%
  cpu          : usr=0.19%, sys=0.05%, ctx=16392, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=32768,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=57.5MiB/s (60.3MB/s), 57.5MiB/s-57.5MiB/s (60.3MB/s-60.3MB/s), io=4096MiB (4295MB), run=71243-71243msec

Disk stats (read/write):
  sda: ios=32715/18, merge=0/18, ticks=69880/164, in_queue=70028, util=98.12%

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
./fio --filename=test --rw=write --ioengine=posixaio --direct=1 --blocksize=128K --size=4G --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=write, bs=(R) 128KiB-128KiB, (W) 128KiB-128KiB, (T) 128KiB-128KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [W(1)][100.0%][r=0KiB/s,w=236MiB/s][r=0,w=1886 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=10508: Thu Oct  5 15:59:11 2017
  write: IOPS=1812, BW=227MiB/s (238MB/s)(4096MiB/18081msec)
    slat (usec): min=3, max=1932, avg=10.99, stdev=16.08
    clat (usec): min=13105, max=40006, avg=17512.41, stdev=1629.50
     lat (usec): min=13114, max=40016, avg=17523.40, stdev=1629.99
    clat percentiles (usec):
     |  1.00th=[15008],  5.00th=[15664], 10.00th=[15926], 20.00th=[16450],
     | 30.00th=[16909], 40.00th=[17171], 50.00th=[17433], 60.00th=[17695],
     | 70.00th=[17957], 80.00th=[18482], 90.00th=[19006], 95.00th=[19792],
     | 99.00th=[22414], 99.50th=[25297], 99.90th=[38536], 99.95th=[39060],
     | 99.99th=[40109]
   bw (  KiB/s): min=212992, max=245760, per=100.00%, avg=232097.22, stdev=9763.83, samples=36
   iops        : min= 1664, max= 1920, avg=1813.22, stdev=76.31, samples=36
  lat (msec)   : 20=96.65%, 50=3.35%
  cpu          : usr=3.01%, sys=0.35%, ctx=16385, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,32768,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=227MiB/s (238MB/s), 227MiB/s-227MiB/s (238MB/s-238MB/s), io=4096MiB (4295MB), run=18081-18081msec

Disk stats (read/write):
  vda: ios=57/32444, merge=0/99, ticks=64/15864, in_queue=15900, util=88.10%
```

*file-size*
```
ls -al test 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 15:59 test
```

*reads*
```
./fio --filename=test --rw=read --ioengine=posixaio --direct=1 --blocksize=128K --runtime=300 --iodepth=32 --group_reporting --name=myjob
myjob: (g=0): rw=read, bs=(R) 128KiB-128KiB, (W) 128KiB-128KiB, (T) 128KiB-128KiB, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=144MiB/s,w=0KiB/s][r=1153,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=10521: Thu Oct  5 15:59:51 2017
   read: IOPS=1385, BW=173MiB/s (182MB/s)(4096MiB/23643msec)
    slat (nsec): min=215, max=155656, avg=1087.56, stdev=3154.19
    clat (usec): min=15226, max=45777, avg=23043.36, stdev=4443.57
     lat (usec): min=15227, max=45779, avg=23044.44, stdev=4443.63
    clat percentiles (usec):
     |  1.00th=[16188],  5.00th=[17171], 10.00th=[17957], 20.00th=[19268],
     | 30.00th=[20055], 40.00th=[21365], 50.00th=[22414], 60.00th=[23462],
     | 70.00th=[24773], 80.00th=[26608], 90.00th=[29230], 95.00th=[31065],
     | 99.00th=[36963], 99.50th=[38011], 99.90th=[42206], 99.95th=[42206],
     | 99.99th=[44303]
   bw (  KiB/s): min=131072, max=212992, per=100.00%, avg=177617.55, stdev=16766.76, samples=47
   iops        : min= 1024, max= 1664, avg=1387.62, stdev=130.98, samples=47
  lat (msec)   : 20=28.28%, 50=71.72%
  cpu          : usr=0.96%, sys=0.24%, ctx=16391, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=32768,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=173MiB/s (182MB/s), 173MiB/s-173MiB/s (182MB/s-182MB/s), io=4096MiB (4295MB), run=23643-23643msec

Disk stats (read/write):
  vda: ios=32562/6, merge=0/10, ticks=21464/0, in_queue=21440, util=91.25%
```
