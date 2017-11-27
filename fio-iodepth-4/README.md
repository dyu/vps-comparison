## Setup
```sh
mkdir -p tmp/tars/fio-bin

wget 'https://onedrive.live.com/download?cid=73A9A646B31A141F&resid=73A9A646B31A141F%21313&authkey=AKuD8CFKysOnqiI' -O tmp/tars/fio-bin.tar.gz

cd tmp/tars && tar -xvzf fio-bin.tar.gz && mv bin fio-bin
cd .. && ln -s tars/fio-bin/fio fio
```
