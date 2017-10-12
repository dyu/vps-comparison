### ops/sec summary on ubuntu 16.04 x64

```
GJ = generate json @ 10M iterations

PJ = parse json @ 10M iterations

EJ = echo @ 10M iterations
     json deser + ser

```

```
                             GJ            PJ             EJ

aws ec2 micro - 990M         2,478,975     1,648,869      1,367,178

gcloud micro  - 585M         2,336,955     1,518,835      1,324,719

vultr         - 488M         1,891,625     1,151,959      1,059,145

linode        - 989M         1,896,259     1,252,841      1,145,792

upcloud       - 992M         3,034,827     1,939,316      1,663,171
```

---

All operations below include overhead of parsing/generating json from/to java objects.
```
I = insert @ 10M iterations
    159MB on disk, inserts 1 primary key and 1 secondary key per iteration

G = get @ 10M iterations
    no disk seeks, same key used per iteration, the sst will be cached by the filesystem

L = list @ 1M iterations
    30 entries fetched per iteration, reverse scan, latest first
```

## leveldb
```
                             I             G             L

aws ec2 micro - 990M         119,492       212,111       26,952

gcloud micro  - 585M         19,386        48,206        5,769

vultr         - 488M         85,007        154,638       21,456

linode        - 989M         104,550       165,869       24,194

upcloud       - 992M         146,642       238,544       33,914
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

