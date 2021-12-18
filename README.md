# nginx-benchmark

## run server

```bash
docker-compose --compatibility -p nb up -d --build
```

## benchmark

<http://192.168.2.201:19999>

```bash
# http1.1 and close
ab -c 100 -n 100000 -k http://192.168.2.201:60010/

This is ApacheBench, Version 2.3 <$Revision: 1879490 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 192.168.2.201 (be patient)
Completed 10000 requests
Completed 20000 requests
Completed 30000 requests
Completed 40000 requests
Completed 50000 requests
Completed 60000 requests
Completed 70000 requests
Completed 80000 requests
Completed 90000 requests
Completed 100000 requests
Finished 100000 requests


Server Software:        nginx/1.21.4
Server Hostname:        192.168.2.201
Server Port:            60010

Document Path:          /
Document Length:        615 bytes

Concurrency Level:      100
Time taken for tests:   68.287 seconds
Complete requests:      100000
Failed requests:        0
Keep-Alive requests:    99956
Total transferred:      85299780 bytes
HTML transferred:       61500000 bytes
Requests per second:    1464.40 [#/sec] (mean)
Time per request:       68.287 [ms] (mean)
Time per request:       0.683 [ms] (mean, across all concurrent requests)
Transfer rate:          1219.86 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.9      0     108
Processing:     5   68  64.5     36     310
Waiting:        3   68  64.5     36     310
Total:          5   68  64.5     36     310

Percentage of the requests served within a certain time (ms)
  50%     36
  66%     40
  75%     58
  80%    118
  90%    194
  95%    209
  98%    227
  99%    262
 100%    310 (longest request)

```

```bash
# http1.1 and keeplive
ab -c 100 -n 100000 -k http://192.168.2.201:60011/

This is ApacheBench, Version 2.3 <$Revision: 1879490 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 192.168.2.201 (be patient)
Completed 10000 requests
Completed 20000 requests
Completed 30000 requests
Completed 40000 requests
Completed 50000 requests
Completed 60000 requests
Completed 70000 requests
Completed 80000 requests
Completed 90000 requests
Completed 100000 requests
Finished 100000 requests


Server Software:        nginx/1.21.4
Server Hostname:        192.168.2.201
Server Port:            60011

Document Path:          /
Document Length:        615 bytes

Concurrency Level:      100
Time taken for tests:   36.549 seconds
Complete requests:      100000
Failed requests:        0
Keep-Alive requests:    99952
Total transferred:      85299760 bytes
HTML transferred:       61500000 bytes
Requests per second:    2736.05 [#/sec] (mean)
Time per request:       36.549 [ms] (mean)
Time per request:       0.365 [ms] (mean, across all concurrent requests)
Transfer rate:          2279.15 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.9      0      41
Processing:     8   36  18.0     34     654
Waiting:        5   36  18.0     34     654
Total:          8   37  18.1     34     654

Percentage of the requests served within a certain time (ms)
  50%     34
  66%     35
  75%     36
  80%     37
  90%     40
  95%     51
  98%     89
  99%    114
 100%    654 (longest request)

```

## exec container
```bash
docker exec -it nb_ngc_1 bash
docker exec -it nb_isc_1 bash

docker exec -it nb_ngk_1 bash
docker exec -it nb_isk_1 bash
```