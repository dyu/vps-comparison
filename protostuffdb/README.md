This benchmark measures raw perf of cpu (serialization) and memory (gc pressure)

### Setup
```sh
mkdir -p tmp/tars/todo-linux-bench-x64

# if the machine's jvm resides in /usr/lib/jvm/java-7-oracle 
wget 'https://onedrive.live.com/download?cid=73A9A646B31A141F&resid=73A9A646B31A141F%21326&authkey=ANMSnjyIKXHdaf4' -O tmp/tars/todo-linux-bench-x64.tar.gz
# else
wget 'https://onedrive.live.com/download?cid=73A9A646B31A141F&resid=73A9A646B31A141F%21327&authkey=ADnsfTGjehRsr7I' -O tmp/tars/todo-linux-bench-x64.tar.gz

cd tmp/tars/todo-linux-bench-x64
tar -xzf ../todo-linux-bench-x64.tar.gz
```

### test echo via curl
```sh
cd bench
./run.sh

# on another terminal
curl http://127.0.0.1:5000/todo/user/echoInt -X POST -d @payload/echoInt.json
```

### test bench echo
```sh
# 1M iterations, 1K warmups
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json 1000000 1000
```

Results
=======

### ops/sec summary on ubuntu 16.04 x64

```
GJ = generate json @ 10M iterations

PJ = parse json @ 10M iterations

EJ = echo json @ 10M iterations
     json deser + ser

```

```
                                 GJ            PJ             EJ

aws ec2 micro     - 990M         2,478,975     1,648,869      1,367,178

gcloud micro      - 585M         2,336,955     1,518,835      1,324,719

vultr             - 488M         1,891,625     1,151,959      1,059,145

linode            - 989M         1,896,259     1,252,841      1,145,792

upcloud           - 992M         3,034,827     1,939,316      1,663,171

impactvps ovz sea - 1024M        2,190,427     1,203,466      1,076,456

itldc lax         - 992M         2,173,074     1,389,370      1,129,998

launchvps lax     - 2000M        3,051,870     1,703,880      1,623,692

hiformance lax    - 2000M        2,819,537     1,152,956      966,843

hosthatch lax     - 992M         2,712,548     1,580,050      1,305,143

hosthatch-s lax   - 992M         2,452,044     1,540,957      1,369,353

ovh sg            - 968M         3,474,082     2,169,417      1,956,535
```

---

All operations below include overhead of parsing/generating json from/to java objects.
```
I = insert @ 10M iterations
    159MB on disk, inserts 1 primary key (9 bytes) and 1 secondary key (15 bytes) per iteration

G = get @ 10M iterations
    no disk seeks, same key used per iteration, the sst will be cached by the filesystem

L = list @ 1M iterations
    30 entries fetched per iteration, reverse scan, latest first
```

## leveldb
```
                               I             G             L

aws ec2 micro   - 990M         119,492       212,111       26,952

gcloud micro    - 585M         19,386        48,206        5,769

vultr           - 488M         85,007        154,638       21,456

linode          - 989M         104,550       165,869       24,194

upcloud         - 992M         146,642       238,544       33,914

impactvps ovz   - 1024M        133,686       156,647       23,581

itldc lax       - 992M         95,673        171,804       24,007

launchvps lax   - 2000M        196,956       247,433       34,595

hiformance lax  - 2000M        146,097       154,510       25,383

hosthatch  lax  - 992M         76,569        158,252       25,604

hosthatch-s lax - 992M         121,784       146,021       25,259
```

## leveldb with replication log (5M iterations on I)
```
                             I             G             L

aws ec2 micro - 990M         66,695        204,882       25,956

gcloud micro  - 585M         10,693        33,150        4,504

vultr         - 488M         51,353        171,654       21,710

linode        - 989M         57,923        162,294       22,366

upcloud       - 992M         71,251        252,838       31,932
```

## hyperleveldb
```
                             I             G             L

aws ec2 micro - 990M         81,731        184,985       29,651

gcloud micro  - 585M         13,679        43,940        7,351

vultr         - 488M         63,903        164,517       27,721

linode        - 989M         69,427        162,366       32,209

upcloud       - 992M         82,308        197,457       37,900
```

## hyperleveldb with replication log (5M iterations on I)
```
                             I             G             L

aws ec2 micro - 990M         58,778        142,950       33,860

gcloud micro  - 585M         9,667         28,883        18,988

vultr         - 488M         45,474        121,343       26,368

linode        - 989M         49,610        136,037       30,823

upcloud       - 992M         58,859        175,339       41,119
```

