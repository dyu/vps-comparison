## Setup
```sh
sudo apt-get install libaio-dev libnuma-dev

mkdir -p tmp/tars

wget 'https://onedrive.live.com/download?cid=73A9A646B31A141F&resid=73A9A646B31A141F%21313&authkey=AKuD8CFKysOnqiI' -O tmp/tars/fio-bin.tar.gz

cd tmp/tars && tar -xvzf fio-bin.tar.gz && mv bin fio-bin
cd .. && ln -s tars/fio-bin/fio fio
```

# Results

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

ovh sg        - 968M                                            22.1k  58.3k  21.8k  38.0k  10.6k/15.9k

itldc lax     - 992M                                            60.5k  90.2k  47.1k  132k   31.2k/46.8k

impactvps ovz - 1024M                                           18.8k  70.1k  5642   8716   4556/6849

launchvps lax - 2000M                                           35.7k  27.1k  26.1k  142k   4920/7366
```

