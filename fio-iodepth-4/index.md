### fio iops summary on ubuntu 16.04 x64

```
SW = sequential write
SR = sequentail read
RW = random write
RR = random read
MRRW = mixed random read/write
```

```
                    posixaio SW     SR     RW     RR     libaio SW     SR     RW     RR     MRRW (40/60)

aws ec2 micro - 990M         434    130    1453   7179          3068   3070   3065   5269   1229/1840

gcloud micro  - 585M         1279   1384   1103   217           5030   3846   1492   736    229/344

vultr         - 488M         8621   8839   7639   5682          28.8k  18.2k  26.9k  26.0k  9346/14.0k

linode        - 989M         9230   10.9k  5616   14.5k         30.3k  39.0k  9701   47.5k  13.4k/20.1k

upcloud       - 992M         6310   12.1k  3585   16.9k         17.6k  47.7k  13.3k  80.7k  13.2k/19.8k
```

