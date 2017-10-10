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
```

## gcloud micro - 585M
```
```

## vultr - 488M
```
```

## linode - 989M
```
```

## upcloud - 992M (/usr/bin/python missing, install via: apt-get install python)
```
```

