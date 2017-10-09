# echo results (all vps run on ubuntu 16.04 x64)

10M iterations

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

