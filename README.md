# nginx-benchmark

## run server

```bash
docker-compose up -d --build
```

## benchmark

监控 <http://192.168.2.201:19999>


```bash
docker exec -it internal bash

# ab 跑完后再停止抓包
tcpdump -w internal.pcap

docker cp internal:/internal.pcap internal.pcap
```

[http1.1 and keeplive](ab-result/http1.1.log)
```bash
ab -c 100 -n 200000 -k http://192.168.2.201:60080/http1.1

Requests per second:    23247.32 [#/sec] (mean)

Percentage of the requests served within a certain time (ms)
  50%      4
  66%      6
  75%      8
  80%      8
  90%     10
  95%     12
  98%     14
  99%     16
 100%     32 (longest request)
```

[http1.0 and close](ab-result/http1.0.log)
```bash
ab -c 100 -n 200000 -k http://192.168.2.201:60080/http1.0

Requests per second:    13778.78 [#/sec] (mean)

Percentage of the requests served within a certain time (ms)
  50%      6
  66%     10
  75%     13
  80%     14
  90%     17
  95%     19
  98%     21
  99%     25
 100%     47 (longest request)
```

![监控](img/netdata.png)
![wireshark io graph](img/wireshark-io-graph.png)

# reference

<https://www.nginx.com/blog/tuning-nginx/>