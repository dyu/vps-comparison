# fio results (all on ubuntu 16.04 x64)
```
# random writes
fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=32 --numjobs=1 --group_reporting --name=myjob --size=4G

# random reads
fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=32 --numjobs=1 --group_reporting --name=myjob
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
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=32 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=6150KiB/s][r=0,w=1537 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18929: Thu Oct  5 19:25:51 2017
  write: IOPS=1480, BW=5922KiB/s (6064kB/s)(1735MiB/300015msec)
    slat (nsec): min=205, max=66141, avg=559.11, stdev=365.45
    clat (usec): min=12502, max=95654, avg=21597.69, stdev=7812.57
     lat (usec): min=12502, max=95656, avg=21598.25, stdev=7812.57
    clat percentiles (usec):
     |  1.00th=[15270],  5.00th=[15533], 10.00th=[15795], 20.00th=[15926],
     | 30.00th=[16188], 40.00th=[16450], 50.00th=[16909], 60.00th=[17695],
     | 70.00th=[27919], 80.00th=[29230], 90.00th=[31065], 95.00th=[36439],
     | 99.00th=[43779], 99.50th=[47973], 99.90th=[58459], 99.95th=[70779],
     | 99.99th=[91751]
   bw (  KiB/s): min= 4096, max= 7128, per=99.99%, avg=5921.40, stdev=384.35, samples=600
   iops        : min= 1024, max= 1782, avg=1480.33, stdev=96.08, samples=600
  lat (msec)   : 20=64.65%, 50=34.98%, 100=0.37%
  cpu          : usr=0.38%, sys=0.10%, ctx=222126, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,444192,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=5922KiB/s (6064kB/s), 5922KiB/s-5922KiB/s (6064kB/s-6064kB/s), io=1735MiB (1819MB), run=300015-300015msec

Disk stats (read/write):
  xvda: ios=0/446585, merge=0/17185, ticks=0/309868, in_queue=309860, util=99.22%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 19:25 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=32 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=36.8MiB/s,w=0KiB/s][r=9420,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=18937: Thu Oct  5 19:31:42 2017
   read: IOPS=7799, BW=30.5MiB/s (31.9MB/s)(4096MiB/134433msec)
    slat (nsec): min=168, max=64504, avg=303.30, stdev=210.40
    clat (usec): min=317, max=33537, avg=4094.94, stdev=1603.13
     lat (usec): min=317, max=33538, avg=4095.25, stdev=1603.13
    clat percentiles (usec):
     |  1.00th=[ 1680],  5.00th=[ 2245], 10.00th=[ 2573], 20.00th=[ 2966],
     | 30.00th=[ 3294], 40.00th=[ 3556], 50.00th=[ 3851], 60.00th=[ 4146],
     | 70.00th=[ 4490], 80.00th=[ 4948], 90.00th=[ 5735], 95.00th=[ 6652],
     | 99.00th=[ 9896], 99.50th=[11469], 99.90th=[17171], 99.95th=[21365],
     | 99.99th=[25035]
   bw (  KiB/s): min=21920, max=39048, per=99.95%, avg=31182.87, stdev=3815.92, samples=268
   iops        : min= 5480, max= 9762, avg=7795.69, stdev=953.98, samples=268
  lat (usec)   : 500=0.01%, 750=0.01%, 1000=0.03%
  lat (msec)   : 2=2.60%, 4=52.58%, 10=43.84%, 20=0.86%, 50=0.06%
  cpu          : usr=1.15%, sys=0.62%, ctx=523974, majf=0, minf=17
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=6.4%, 16=68.6%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=95.6%, 8=1.9%, 16=0.1%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=30.5MiB/s (31.9MB/s), 30.5MiB/s-30.5MiB/s (31.9MB/s-31.9MB/s), io=4096MiB (4295MB), run=134433-134433msec

Disk stats (read/write):
  xvda: ios=360928/10, merge=0/9, ticks=132776/0, in_queue=132764, util=98.78%
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
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=32 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=3712KiB/s][r=0,w=928 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=1000: Thu Oct  5 19:26:03 2017
  write: IOPS=877, BW=3512KiB/s (3596kB/s)(1029MiB/300020msec)
    slat (nsec): min=138, max=158893, avg=759.72, stdev=1220.39
    clat (msec): min=17, max=204, avg=36.43, stdev=14.95
     lat (msec): min=17, max=204, avg=36.43, stdev=14.95
    clat percentiles (msec):
     |  1.00th=[   20],  5.00th=[   21], 10.00th=[   23], 20.00th=[   26],
     | 30.00th=[   28], 40.00th=[   31], 50.00th=[   33], 60.00th=[   37],
     | 70.00th=[   41], 80.00th=[   46], 90.00th=[   55], 95.00th=[   64],
     | 99.00th=[   86], 99.50th=[  102], 99.90th=[  165], 99.95th=[  180],
     | 99.99th=[  203]
   bw (  KiB/s): min= 1280, max= 6400, per=100.00%, avg=3511.52, stdev=987.16, samples=600
   iops        : min=  320, max= 1600, avg=877.87, stdev=246.79, samples=600
  lat (msec)   : 20=2.71%, 50=83.36%, 100=13.41%, 250=0.52%
  cpu          : usr=0.34%, sys=0.07%, ctx=131741, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,263392,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3512KiB/s (3596kB/s), 3512KiB/s-3512KiB/s (3596kB/s-3596kB/s), io=1029MiB (1079MB), run=300020-300020msec

Disk stats (read/write):
  sda: ios=0/267812, merge=0/59804, ticks=0/301000, in_queue=300876, util=96.13%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 19:26 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=32 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=1276KiB/s,w=0KiB/s][r=319,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=1024: Thu Oct  5 19:33:50 2017
   read: IOPS=262, BW=1052KiB/s (1077kB/s)(308MiB/300025msec)
    slat (nsec): min=101, max=170163, avg=534.11, stdev=1396.99
    clat (usec): min=224, max=301512, avg=121688.15, stdev=45281.28
     lat (usec): min=228, max=301512, avg=121688.68, stdev=45281.27
    clat percentiles (msec):
     |  1.00th=[   33],  5.00th=[   54], 10.00th=[   67], 20.00th=[   83],
     | 30.00th=[   95], 40.00th=[  108], 50.00th=[  120], 60.00th=[  130],
     | 70.00th=[  142], 80.00th=[  159], 90.00th=[  182], 95.00th=[  203],
     | 99.00th=[  247], 99.50th=[  257], 99.90th=[  271], 99.95th=[  275],
     | 99.99th=[  292]
   bw (  KiB/s): min=  512, max= 1792, per=100.00%, avg=1051.32, stdev=219.78, samples=600
   iops        : min=  128, max=  448, avg=262.82, stdev=54.95, samples=600
  lat (usec)   : 250=0.01%, 500=0.01%
  lat (msec)   : 2=0.01%, 10=0.03%, 20=0.20%, 50=3.68%, 100=30.04%
  lat (msec)   : 250=65.19%, 500=0.84%
  cpu          : usr=0.10%, sys=0.02%, ctx=39445, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=78880,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1052KiB/s (1077kB/s), 1052KiB/s-1052KiB/s (1077kB/s-1077kB/s), io=308MiB (323MB), run=300025-300025msec

Disk stats (read/write):
  sda: ios=17564/69, merge=0/50, ticks=297736/268, in_queue=298000, util=99.30%
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
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=32 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=34.5MiB/s][r=0,w=8837 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11872: Thu Oct  5 19:23:39 2017
  write: IOPS=8667, BW=33.9MiB/s (35.5MB/s)(4096MiB/120979msec)
    slat (nsec): min=218, max=4655.6k, avg=770.69, stdev=4694.42
    clat (usec): min=2190, max=57714, avg=3670.78, stdev=1360.36
     lat (usec): min=2190, max=57715, avg=3671.55, stdev=1360.43
    clat percentiles (usec):
     |  1.00th=[ 2573],  5.00th=[ 2835], 10.00th=[ 2999], 20.00th=[ 3195],
     | 30.00th=[ 3294], 40.00th=[ 3392], 50.00th=[ 3490], 60.00th=[ 3621],
     | 70.00th=[ 3752], 80.00th=[ 3982], 90.00th=[ 4359], 95.00th=[ 4817],
     | 99.00th=[ 6259], 99.50th=[ 7504], 99.90th=[19792], 99.95th=[41681],
     | 99.99th=[48497]
   bw (  KiB/s): min=23256, max=42240, per=99.99%, avg=34665.89, stdev=2918.11, samples=241
   iops        : min= 5814, max=10560, avg=8666.46, stdev=729.53, samples=241
  lat (msec)   : 4=80.46%, 10=19.29%, 20=0.16%, 50=0.09%, 100=0.01%
  cpu          : usr=2.66%, sys=1.08%, ctx=524385, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=33.9MiB/s (35.5MB/s), 33.9MiB/s-33.9MiB/s (35.5MB/s-35.5MB/s), io=4096MiB (4295MB), run=120979-120979msec

Disk stats (read/write):
  vda: ios=1/1054473, merge=0/59581, ticks=0/111840, in_queue=111600, util=75.99%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 19:23 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=32 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][100.0%][r=24.4MiB/s,w=0KiB/s][r=6249,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=11903: Thu Oct  5 19:30:35 2017
   read: IOPS=6430, BW=25.1MiB/s (26.3MB/s)(4096MiB/163075msec)
    slat (nsec): min=198, max=1334.9k, avg=646.66, stdev=1978.57
    clat (usec): min=2014, max=42404, avg=4952.98, stdev=1169.69
     lat (usec): min=2014, max=42405, avg=4953.62, stdev=1169.75
    clat percentiles (usec):
     |  1.00th=[ 3163],  5.00th=[ 3589], 10.00th=[ 3851], 20.00th=[ 4178],
     | 30.00th=[ 4424], 40.00th=[ 4621], 50.00th=[ 4817], 60.00th=[ 5080],
     | 70.00th=[ 5276], 80.00th=[ 5604], 90.00th=[ 6063], 95.00th=[ 6587],
     | 99.00th=[ 8029], 99.50th=[ 9241], 99.90th=[16319], 99.95th=[21627],
     | 99.99th=[33817]
   bw (  KiB/s): min=18376, max=32256, per=100.00%, avg=25723.23, stdev=2235.12, samples=326
   iops        : min= 4594, max= 8064, avg=6430.80, stdev=558.78, samples=326
  lat (msec)   : 4=14.14%, 10=85.50%, 20=0.30%, 50=0.06%
  cpu          : usr=2.12%, sys=0.99%, ctx=524412, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=25.1MiB/s (26.3MB/s), 25.1MiB/s-25.1MiB/s (26.3MB/s-26.3MB/s), io=4096MiB (4295MB), run=163075-163075msec

Disk stats (read/write):
  vda: ios=662114/27, merge=0/11, ticks=142572/0, in_queue=142396, util=87.41%
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
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=32 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=25.0MiB/s][r=0,w=6411 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=5029: Thu Oct  5 19:25:16 2017
  write: IOPS=4305, BW=16.8MiB/s (17.6MB/s)(4096MiB/243537msec)
    slat (nsec): min=232, max=258578, avg=743.81, stdev=1233.19
    clat (msec): min=2, max=11008, avg= 7.41, stdev=87.21
     lat (msec): min=2, max=11008, avg= 7.41, stdev=87.21
    clat percentiles (msec):
     |  1.00th=[    3],  5.00th=[    3], 10.00th=[    3], 20.00th=[    4],
     | 30.00th=[    4], 40.00th=[    4], 50.00th=[    4], 60.00th=[    4],
     | 70.00th=[    4], 80.00th=[    5], 90.00th=[    5], 95.00th=[    6],
     | 99.00th=[   75], 99.50th=[  140], 99.90th=[  852], 99.95th=[ 1301],
     | 99.99th=[ 2668]
   bw (  KiB/s): min=  200, max=42952, per=100.00%, avg=22007.07, stdev=8306.51, samples=381
   iops        : min=   50, max=10738, avg=5501.75, stdev=2076.63, samples=381
  lat (msec)   : 4=71.36%, 10=27.42%, 20=0.01%, 50=0.01%, 100=0.44%
  lat (msec)   : 250=0.53%, 500=0.05%, 750=0.05%, 1000=0.06%, 2000=0.05%
  lat (msec)   : >=2000=0.03%
  cpu          : usr=1.41%, sys=0.71%, ctx=524391, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=16.8MiB/s (17.6MB/s), 16.8MiB/s-16.8MiB/s (17.6MB/s-17.6MB/s), io=4096MiB (4295MB), run=243537-243537msec

Disk stats (read/write):
  sda: ios=8/1171538, merge=0/398346, ticks=393/301293, in_queue=300867, util=79.06%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 19:25 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=32 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][10.0%][r=69.9MiB/s,w=0KiB/s][r=17.9k,w=0 IOPS][eta 00m:54sJobs: 1 (f=1): [r(1)][11.5%][r=65.1MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:54sJobs: 1 (f=1): [r(1)][13.1%][r=67.2MiB/s,w=0KiB/s][r=17.2k,w=0 IOPS][eta 00m:53sJobs: 1 (f=1): [r(1)][15.0%][r=69.4MiB/s,w=0KiB/s][r=17.8k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [r(1)][16.4%][r=64.4MiB/s,w=0KiB/s][r=16.5k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [r(1)][18.0%][r=67.0MiB/s,w=0KiB/s][r=17.2k,w=0 IOPS][eta 00m:50sJobs: 1 (f=1): [r(1)][19.7%][r=65.7MiB/s,w=0KiB/s][r=16.8k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [r(1)][21.3%][r=69.8MiB/s,w=0KiB/s][r=17.9k,w=0 IOPS][eta 00m:48sJobs: 1 (f=1): [r(1)][23.0%][r=64.7MiB/s,w=0KiB/s][r=16.6k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [r(1)][25.0%][r=76.9MiB/s,w=0KiB/s][r=19.7k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [r(1)][26.7%][r=64.3MiB/s,w=0KiB/s][r=16.5k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [r(1)][28.3%][r=66.0MiB/s,w=0KiB/s][r=16.9k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [r(1)][30.0%][r=68.4MiB/s,w=0KiB/s][r=17.5k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [r(1)][31.7%][r=70.0MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [r(1)][33.3%][r=70.8MiB/s,w=0KiB/s][r=18.1k,w=0 IOPS][eta 00m:40sJobs: 1 (f=1): [r(1)][35.0%][r=65.1MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [r(1)][36.7%][r=70.9MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [r(1)][38.3%][r=68.4MiB/s,w=0KiB/s][r=17.5k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [r(1)][40.0%][r=67.4MiB/s,w=0KiB/s][r=17.3k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [r(1)][41.7%][r=59.2MiB/s,w=0KiB/s][r=15.2k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [r(1)][42.6%][r=57.9MiB/s,w=0KiB/s][r=14.8k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [r(1)][45.0%][r=87.1MiB/s,w=0KiB/s][r=22.3k,w=0 IOPS][eta 00m:33sJobs: 1 (f=1): [r(1)][47.5%][r=92.2MiB/s,w=0KiB/s][r=23.6k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [r(1)][49.2%][r=88.2MiB/s,w=0KiB/s][r=22.6k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][51.7%][r=90.5MiB/s,w=0KiB/s][r=23.2k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [r(1)][53.4%][r=72.6MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [r(1)][55.2%][r=71.6MiB/s,w=0KiB/s][r=18.3k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [r(1)][56.9%][r=78.6MiB/s,w=0KiB/s][r=20.1k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [r(1)][58.6%][r=76.4MiB/s,w=0KiB/s][r=19.5k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [r(1)][61.4%][r=76.6MiB/s,w=0KiB/s][r=19.6k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [r(1)][63.2%][r=72.4MiB/s,w=0KiB/s][r=18.5k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [r(1)][64.9%][r=74.4MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [r(1)][66.7%][r=67.8MiB/s,w=0KiB/s][r=17.4k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [r(1)][68.4%][r=74.4MiB/s,w=0KiB/s][r=19.0k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [r(1)][70.2%][r=93.1MiB/s,w=0KiB/s][r=23.8k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [r(1)][71.9%][r=85.5MiB/s,w=0KiB/s][r=21.9k,w=0 IOPS][eta 00m:16sJobs: 1 (f=1): [r(1)][73.7%][r=73.3MiB/s,w=0KiB/s][r=18.8k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [r(1)][76.8%][r=85.9MiB/s,w=0KiB/s][r=21.0k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [r(1)][78.6%][r=65.9MiB/s,w=0KiB/s][r=16.9k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [r(1)][80.4%][r=82.8MiB/s,w=0KiB/s][r=21.2k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [r(1)][82.1%][r=93.5MiB/s,w=0KiB/s][r=23.9k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [r(1)][85.5%][r=94.0MiB/s,w=0KiB/s][r=24.3k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [r(1)][87.3%][r=93.0MiB/s,w=0KiB/s][r=24.1k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [r(1)][89.1%][r=87.0MiB/s,w=0KiB/s][r=22.5k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [r(1)][90.9%][r=65.2MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [r(1)][92.7%][r=73.6MiB/s,w=0KiB/s][r=18.8k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [r(1)][94.5%][r=72.6MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [r(1)][96.4%][r=78.9MiB/s,w=0KiB/s][r=20.2k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [r(1)][98.2%][r=79.7MiB/s,w=0KiB/s][r=20.4k,w=0 IOPS][eta 00m:01sJobs: 1 (f=1): [r(1)][100.0%][r=71.8MiB/s,w=0KiB/s][r=18.4k,w=0 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=5041: Thu Oct  5 19:27:56 2017
   read: IOPS=18.0k, BW=74.0MiB/s (77.6MB/s)(4096MiB/55327msec)
    slat (nsec): min=195, max=366516, avg=401.44, stdev=771.66
    clat (usec): min=591, max=10572, avg=1675.56, stdev=414.79
     lat (usec): min=591, max=10573, avg=1675.96, stdev=414.84
    clat percentiles (usec):
     |  1.00th=[ 1020],  5.00th=[ 1156], 10.00th=[ 1237], 20.00th=[ 1352],
     | 30.00th=[ 1450], 40.00th=[ 1532], 50.00th=[ 1614], 60.00th=[ 1696],
     | 70.00th=[ 1811], 80.00th=[ 1942], 90.00th=[ 2180], 95.00th=[ 2376],
     | 99.00th=[ 3032], 99.50th=[ 3425], 99.90th=[ 4359], 99.95th=[ 4948],
     | 99.99th=[ 6915]
   bw (  KiB/s): min=57576, max=99328, per=99.99%, avg=75803.68, stdev=10442.85, samples=110
   iops        : min=14394, max=24832, avg=18950.91, stdev=2610.72, samples=110
  lat (usec)   : 750=0.01%, 1000=0.73%
  lat (msec)   : 2=82.54%, 4=16.56%, 10=0.17%, 20=0.01%
  cpu          : usr=3.95%, sys=2.12%, ctx=524376, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=74.0MiB/s (77.6MB/s), 74.0MiB/s-74.0MiB/s (77.6MB/s-77.6MB/s), io=4096MiB (4295MB), run=55327-55327msec

Disk stats (read/write):
  sda: ios=660911/0, merge=0/0, ticks=31207/0, in_queue=31020, util=56.18%
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
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randwrite --iodepth=32 --numjobs=1 --group_reporting --name=myjob --size=4G
myjob: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
myjob: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [w(1)][100.0%][r=0KiB/s,w=17.0MiB/s][r=0,w=4605 IOPS][eta 00m:00s]
myjob: (groupid=0, jobs=1): err= 0: pid=16810: Thu Oct  5 19:24:25 2017
  write: IOPS=5633, BW=22.0MiB/s (23.1MB/s)(4096MiB/186130msec)
    slat (nsec): min=196, max=65684, avg=438.80, stdev=273.87
    clat (msec): min=3, max=305, avg= 5.67, stdev=13.03
     lat (msec): min=3, max=305, avg= 5.67, stdev=13.03
    clat percentiles (msec):
     |  1.00th=[    4],  5.00th=[    5], 10.00th=[    5], 20.00th=[    5],
     | 30.00th=[    5], 40.00th=[    5], 50.00th=[    5], 60.00th=[    5],
     | 70.00th=[    6], 80.00th=[    6], 90.00th=[    6], 95.00th=[    7],
     | 99.00th=[    9], 99.50th=[   12], 99.90th=[  262], 99.95th=[  271],
     | 99.99th=[  296]
   bw (  KiB/s): min= 4872, max=31976, per=99.99%, avg=22531.33, stdev=5048.50, samples=372
   iops        : min= 1218, max= 7994, avg=5632.83, stdev=1262.13, samples=372
  lat (msec)   : 4=2.05%, 10=97.26%, 20=0.34%, 50=0.02%, 100=0.01%
  lat (msec)   : 250=0.20%, 500=0.12%
  cpu          : usr=0.92%, sys=0.41%, ctx=524346, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=0,1048576,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=22.0MiB/s (23.1MB/s), 22.0MiB/s-22.0MiB/s (23.1MB/s-23.1MB/s), io=4096MiB (4295MB), run=186130-186130msec

Disk stats (read/write):
  vda: ios=0/1065715, merge=0/197202, ticks=0/397016, in_queue=396860, util=92.18%
```

*file-size*
```
ls -al test4Krandom 
-rw-r--r-- 1 deploy deploy 4294967296 Oct  5 19:24 test4Krandom
```

*reads*
```
./fio --filename=test4Krandom --ioengine=posixaio --direct=1 --norandommap --randrepeat=0 --runtime=300 --blocksize=4K --rw=randread --iodepth=32 --numjobs=1 --group_reporting --name=myjob
myjob: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=posixaio, iodepth=32
fio-3.1
Starting 1 process
Jobs: 1 (f=1): [r(1)][10.0%][r=60.9MiB/s,w=0KiB/s][r=15.6k,w=0 IOPS][eta 00m:54sJobs: 1 (f=1): [r(1)][11.5%][r=61.8MiB/s,w=0KiB/s][r=15.8k,w=0 IOPS][eta 00m:54sJobs: 1 (f=1): [r(1)][13.1%][r=65.4MiB/s,w=0KiB/s][r=16.7k,w=0 IOPS][eta 00m:53sJobs: 1 (f=1): [r(1)][15.0%][r=75.1MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:51sJobs: 1 (f=1): [r(1)][16.7%][r=69.4MiB/s,w=0KiB/s][r=17.8k,w=0 IOPS][eta 00m:50sJobs: 1 (f=1): [r(1)][18.3%][r=71.0MiB/s,w=0KiB/s][r=18.2k,w=0 IOPS][eta 00m:49sJobs: 1 (f=1): [r(1)][20.3%][r=81.1MiB/s,w=0KiB/s][r=20.8k,w=0 IOPS][eta 00m:47sJobs: 1 (f=1): [r(1)][22.4%][r=79.9MiB/s,w=0KiB/s][r=20.4k,w=0 IOPS][eta 00m:45sJobs: 1 (f=1): [r(1)][24.1%][r=81.0MiB/s,w=0KiB/s][r=20.7k,w=0 IOPS][eta 00m:44sJobs: 1 (f=1): [r(1)][25.9%][r=69.2MiB/s,w=0KiB/s][r=17.7k,w=0 IOPS][eta 00m:43sJobs: 1 (f=1): [r(1)][27.6%][r=68.0MiB/s,w=0KiB/s][r=17.4k,w=0 IOPS][eta 00m:42sJobs: 1 (f=1): [r(1)][29.3%][r=72.0MiB/s,w=0KiB/s][r=18.4k,w=0 IOPS][eta 00m:41sJobs: 1 (f=1): [r(1)][31.6%][r=77.8MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:39sJobs: 1 (f=1): [r(1)][33.3%][r=83.1MiB/s,w=0KiB/s][r=21.3k,w=0 IOPS][eta 00m:38sJobs: 1 (f=1): [r(1)][35.1%][r=76.1MiB/s,w=0KiB/s][r=19.5k,w=0 IOPS][eta 00m:37sJobs: 1 (f=1): [r(1)][36.8%][r=67.5MiB/s,w=0KiB/s][r=17.3k,w=0 IOPS][eta 00m:36sJobs: 1 (f=1): [r(1)][38.6%][r=72.2MiB/s,w=0KiB/s][r=18.5k,w=0 IOPS][eta 00m:35sJobs: 1 (f=1): [r(1)][40.4%][r=76.6MiB/s,w=0KiB/s][r=19.6k,w=0 IOPS][eta 00m:34sJobs: 1 (f=1): [r(1)][42.9%][r=79.1MiB/s,w=0KiB/s][r=20.3k,w=0 IOPS][eta 00m:32sJobs: 1 (f=1): [r(1)][44.6%][r=72.3MiB/s,w=0KiB/s][r=18.5k,w=0 IOPS][eta 00m:31sJobs: 1 (f=1): [r(1)][46.4%][r=68.6MiB/s,w=0KiB/s][r=17.6k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][47.4%][r=69.4MiB/s,w=0KiB/s][r=17.8k,w=0 IOPS][eta 00m:30sJobs: 1 (f=1): [r(1)][50.0%][r=79.4MiB/s,w=0KiB/s][r=20.3k,w=0 IOPS][eta 00m:28sJobs: 1 (f=1): [r(1)][51.8%][r=77.2MiB/s,w=0KiB/s][r=19.8k,w=0 IOPS][eta 00m:27sJobs: 1 (f=1): [r(1)][53.6%][r=79.8MiB/s,w=0KiB/s][r=20.4k,w=0 IOPS][eta 00m:26sJobs: 1 (f=1): [r(1)][55.4%][r=73.6MiB/s,w=0KiB/s][r=18.8k,w=0 IOPS][eta 00m:25sJobs: 1 (f=1): [r(1)][57.1%][r=68.1MiB/s,w=0KiB/s][r=17.4k,w=0 IOPS][eta 00m:24sJobs: 1 (f=1): [r(1)][58.9%][r=72.5MiB/s,w=0KiB/s][r=18.6k,w=0 IOPS][eta 00m:23sJobs: 1 (f=1): [r(1)][60.7%][r=76.0MiB/s,w=0KiB/s][r=19.7k,w=0 IOPS][eta 00m:22sJobs: 1 (f=1): [r(1)][62.5%][r=77.9MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:21sJobs: 1 (f=1): [r(1)][64.3%][r=76.2MiB/s,w=0KiB/s][r=19.5k,w=0 IOPS][eta 00m:20sJobs: 1 (f=1): [r(1)][66.1%][r=75.2MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:19sJobs: 1 (f=1): [r(1)][67.9%][r=75.1MiB/s,w=0KiB/s][r=19.2k,w=0 IOPS][eta 00m:18sJobs: 1 (f=1): [r(1)][69.6%][r=73.8MiB/s,w=0KiB/s][r=18.9k,w=0 IOPS][eta 00m:17sJobs: 1 (f=1): [r(1)][72.7%][r=88.2MiB/s,w=0KiB/s][r=22.6k,w=0 IOPS][eta 00m:15sJobs: 1 (f=1): [r(1)][74.5%][r=73.0MiB/s,w=0KiB/s][r=18.9k,w=0 IOPS][eta 00m:14sJobs: 1 (f=1): [r(1)][76.4%][r=77.2MiB/s,w=0KiB/s][r=19.8k,w=0 IOPS][eta 00m:13sJobs: 1 (f=1): [r(1)][78.2%][r=77.7MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:12sJobs: 1 (f=1): [r(1)][80.0%][r=77.6MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:11sJobs: 1 (f=1): [r(1)][81.8%][r=67.3MiB/s,w=0KiB/s][r=17.2k,w=0 IOPS][eta 00m:10sJobs: 1 (f=1): [r(1)][83.6%][r=68.0MiB/s,w=0KiB/s][r=17.4k,w=0 IOPS][eta 00m:09sJobs: 1 (f=1): [r(1)][85.5%][r=81.4MiB/s,w=0KiB/s][r=20.8k,w=0 IOPS][eta 00m:08sJobs: 1 (f=1): [r(1)][87.3%][r=81.3MiB/s,w=0KiB/s][r=20.8k,w=0 IOPS][eta 00m:07sJobs: 1 (f=1): [r(1)][89.1%][r=91.1MiB/s,w=0KiB/s][r=23.3k,w=0 IOPS][eta 00m:06sJobs: 1 (f=1): [r(1)][90.9%][r=77.8MiB/s,w=0KiB/s][r=19.9k,w=0 IOPS][eta 00m:05sJobs: 1 (f=1): [r(1)][92.7%][r=77.5MiB/s,w=0KiB/s][r=19.8k,w=0 IOPS][eta 00m:04sJobs: 1 (f=1): [r(1)][94.5%][r=78.9MiB/s,w=0KiB/s][r=20.2k,w=0 IOPS][eta 00m:03sJobs: 1 (f=1): [r(1)][96.4%][r=76.6MiB/s,w=0KiB/s][r=19.6k,w=0 IOPS][eta 00m:02sJobs: 1 (f=1): [r(1)][98.2%][r=80.6MiB/s,w=0KiB/s][r=20.6k,w=0 IOPS][eta 00m:01s]
myjob: (groupid=0, jobs=1): err= 0: pid=16816: Thu Oct  5 19:26:37 2017
   read: IOPS=19.1k, BW=74.7MiB/s (78.3MB/s)(4096MiB/54846msec)
    slat (nsec): min=174, max=65319, avg=252.12, stdev=162.79
    clat (usec): min=567, max=62224, avg=1664.90, stdev=525.45
     lat (usec): min=568, max=62224, avg=1665.16, stdev=525.46
    clat percentiles (usec):
     |  1.00th=[ 1057],  5.00th=[ 1221], 10.00th=[ 1303], 20.00th=[ 1418],
     | 30.00th=[ 1500], 40.00th=[ 1565], 50.00th=[ 1631], 60.00th=[ 1696],
     | 70.00th=[ 1778], 80.00th=[ 1876], 90.00th=[ 2024], 95.00th=[ 2180],
     | 99.00th=[ 2638], 99.50th=[ 2933], 99.90th=[ 4555], 99.95th=[ 5538],
     | 99.99th=[19792]
   bw (  KiB/s): min=56888, max=97248, per=99.97%, avg=76450.06, stdev=7327.98, samples=109
   iops        : min=14222, max=24312, avg=19112.51, stdev=1831.99, samples=109
  lat (usec)   : 750=0.01%, 1000=0.37%
  lat (msec)   : 2=87.99%, 4=11.48%, 10=0.14%, 20=0.01%, 50=0.01%
  lat (msec)   : 100=0.01%
  cpu          : usr=2.16%, sys=1.24%, ctx=524329, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=25.0%, 16=50.0%, 32=25.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=97.5%, 8=0.1%, 16=0.0%, 32=2.5%, 64=0.0%, >=64=0.0%
     issued rwt: total=1048576,0,0, short=0,0,0, dropped=0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=74.7MiB/s (78.3MB/s), 74.7MiB/s-74.7MiB/s (78.3MB/s-78.3MB/s), io=4096MiB (4295MB), run=54846-54846msec

Disk stats (read/write):
  vda: ios=660006/3, merge=0/1, ticks=48724/0, in_queue=48656, util=88.90%
```

