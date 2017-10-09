### leveldb ops/sec summary on ubuntu 16.04 x64

```
E = echo @ 10M iterations
C = create @ 10M iterations
G = get @ 10M iterations
L = list @ 1M iterations
```

```
                             E             C             G             L

aws ec2 micro - 990M         1,354,580     91,600        207,723       27,095

gcloud micro  - 585M         1,171,511     15,547        41,274        12,846

vultr         - 488M         1,134,077     64,084        168,141       20,819

linode        - 989M         1,217,685     90,640        147,906       23,904

upcloud       - 992M         1,626,474     119,140       233,946       34,111
```

