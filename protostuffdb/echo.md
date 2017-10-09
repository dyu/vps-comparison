# echo results (all vps run on ubuntu 16.04 x64)

10M iterations
- parses `{"1":123456789}` into a java object and then writes that java object back as json with the same number.

```
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
```

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)
```
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 177 ms | total: 229 ms
elapsed ms: 6,885 | ops/sec: 1,452,325 | response body bytes: 20
```

## aws ec2 micro - 990M
```
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 39 ms | total: 121 ms
elapsed ms: 7,382 | ops/sec: 1,354,580 | response body bytes: 20
```

## gcloud micro - 585M
```
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 42 ms | total: 546 ms
elapsed ms: 8,535 | ops/sec: 1,171,511 | response body bytes: 20
```

## vultr - 488M
```
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 70 ms | total: 314 ms
elapsed ms: 8,817 | ops/sec: 1,134,077 | response body bytes: 20
```

## linode - 989M
```
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 35 ms | total: 214 ms
elapsed ms: 8,212 | ops/sec: 1,217,685 | response body bytes: 20
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
```
./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 39 ms | total: 148 ms
elapsed ms: 6,148 | ops/sec: 1,626,474 | response body bytes: 20
```

