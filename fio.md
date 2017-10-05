## Results for fio-3.1:
```
fio --filename=test --rw=write --ioengine=posixaio --direct=1 --blocksize=128K --size=4G --iodepth=32 --group_reporting --name=myjob

fio --filename=test --rw=read --ioengine=posixaio --direct=1 --blocksize=128K --runtime=300 --iodepth=32 --group_reporting --name=myjob
```

### amazon micro - 990M
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

### gcloud micro - 585M
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

```
*reads*
```

```

### vultr - 488M
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

```
*reads*
```

```
