# serialization results (all vps run on ubuntu 16.04 x64)

10M iterations
- generateInt generates `{"1":123456789}` (no gc overhead, raw jni perf)
- parseInt parses `{"1":123456789}`
- echoInt parses the input like above and writes it back to json
- echoStr is the same as above except the payload is `{"1":"hello world!"}`
- echoKey is the same as above except the payload is `{"1":"AAAAAAAAAAAA"}` (base64-encoded byte array)

## local machine - 15945M (Intel i7 3630qm 2.4 ghz with turboboost to 3.4 ghz)
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 155 ms | total: 207 ms
elapsed ms: 3,311 | ops/sec: 3,019,606 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 178 ms | total: 229 ms
elapsed ms: 5,918 | ops/sec: 1,689,492 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 180 ms | total: 232 ms
elapsed ms: 6,972 | ops/sec: 1,434,116 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 224 ms | total: 276 ms
elapsed ms: 7,146 | ops/sec: 1,399,208 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 169 ms | total: 221 ms
elapsed ms: 8,066 | ops/sec: 1,239,752 | response body bytes: 25
```

## aws ec2 micro - 990M
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 35 ms | total: 118 ms
elapsed ms: 4,033 | ops/sec: 2,478,975 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 33 ms | total: 117 ms
elapsed ms: 6,064 | ops/sec: 1,648,869 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 31 ms | total: 113 ms
elapsed ms: 7,314 | ops/sec: 1,367,178 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 30 ms | total: 112 ms
elapsed ms: 7,568 | ops/sec: 1,321,343 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 33 ms | total: 114 ms
elapsed ms: 8,792 | ops/sec: 1,137,301 | response body bytes: 25
```

## gcloud micro - 585M
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 74 ms | total: 198 ms
elapsed ms: 4,279 | ops/sec: 2,336,955 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 92 ms | total: 189 ms
elapsed ms: 6,583 | ops/sec: 1,518,835 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 46 ms | total: 140 ms
elapsed ms: 7,548 | ops/sec: 1,324,719 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 34 ms | total: 134 ms
elapsed ms: 8,709 | ops/sec: 1,148,210 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 46 ms | total: 144 ms
elapsed ms: 8,966 | ops/sec: 1,115,283 | response body bytes: 25
```

## vultr - 488M
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 98 ms | total: 345 ms
elapsed ms: 5,286 | ops/sec: 1,891,625 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 82 ms | total: 308 ms
elapsed ms: 8,680 | ops/sec: 1,151,959 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 80 ms | total: 270 ms
elapsed ms: 9,441 | ops/sec: 1,059,145 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 92 ms | total: 282 ms
elapsed ms: 10,879 | ops/sec: 919,153 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 82 ms | total: 257 ms
elapsed ms: 11,821 | ops/sec: 845,927 | response body bytes: 25
```

## linode - 989M
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 45 ms | total: 157 ms
elapsed ms: 5,273 | ops/sec: 1,896,259 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 33 ms | total: 139 ms
elapsed ms: 7,981 | ops/sec: 1,252,841 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 47 ms | total: 177 ms
elapsed ms: 8,727 | ops/sec: 1,145,792 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 53 ms | total: 168 ms
elapsed ms: 8,412 | ops/sec: 1,188,765 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 45 ms | total: 164 ms
elapsed ms: 10,991 | ops/sec: 909,775 | response body bytes: 25
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 34 ms | total: 102 ms
elapsed ms: 3,295 | ops/sec: 3,034,827 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 37 ms | total: 104 ms
elapsed ms: 5,156 | ops/sec: 1,939,316 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 31 ms | total: 99 ms
elapsed ms: 6,012 | ops/sec: 1,663,171 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 34 ms | total: 100 ms
elapsed ms: 6,365 | ops/sec: 1,570,928 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 30 ms | total: 96 ms
elapsed ms: 6,933 | ops/sec: 1,442,279 | response body bytes: 25
```

## itldc lax - 992M (/usr/bin/python missing, install via: apt-get install python)
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 60 ms | total: 151 ms
elapsed ms: 4,601 | ops/sec: 2,173,074 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 59 ms | total: 152 ms
elapsed ms: 7,197 | ops/sec: 1,389,370 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 66 ms | total: 166 ms
elapsed ms: 8,849 | ops/sec: 1,129,998 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 72 ms | total: 159 ms
elapsed ms: 8,802 | ops/sec: 1,136,004 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 82 ms | total: 177 ms
elapsed ms: 9,636 | ops/sec: 1,037,725 | response body bytes: 25
```

## impactvps ovz - 1024M (/usr/bin/python missing, install via: apt-get install python)
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 28 ms | total: 105 ms
elapsed ms: 4,565 | ops/sec: 2,190,427 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 28 ms | total: 110 ms
elapsed ms: 8,309 | ops/sec: 1,203,466 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 28 ms | total: 107 ms
elapsed ms: 9,289 | ops/sec: 1,076,456 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 29 ms | total: 107 ms
elapsed ms: 9,834 | ops/sec: 1,016,862 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 31 ms | total: 115 ms
elapsed ms: 10,663 | ops/sec: 937,750 | response body bytes: 25
```

## serverhand dallas - 2000M (/usr/bin/python missing, install via: apt-get install python)
```
./run-uri.sh protostuffdb /todo/user/generateInt /dev/null
protostuffdb
jni rpc: 292 ms | total: 592 ms
elapsed ms: 28,117 | ops/sec: 355,650 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/parseInt payload/echoInt.json
protostuffdb
jni rpc: 297 ms | total: 1013 ms
elapsed ms: 63,609 | ops/sec: 157,209 | response body bytes: 6

./run-uri.sh protostuffdb /todo/user/echoInt payload/echoInt.json
protostuffdb
jni rpc: 186 ms | total: 476 ms
elapsed ms: 69,091 | ops/sec: 144,736 | response body bytes: 20

./run-uri.sh protostuffdb /todo/user/echoStr payload/echoStr.json
protostuffdb
jni rpc: 302 ms | total: 995 ms
elapsed ms: 82,077 | ops/sec: 121,835 | response body bytes: 25

./run-uri.sh protostuffdb /todo/user/echoKey payload/echoKey.json
protostuffdb
jni rpc: 392 ms | total: 1195 ms
elapsed ms: 96,894 | ops/sec: 103,205 | response body bytes: 25
```
