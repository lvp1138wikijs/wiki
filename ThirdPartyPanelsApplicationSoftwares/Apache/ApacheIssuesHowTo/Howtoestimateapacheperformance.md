---
title: How to estimate apache performance
description: 
published: true
date: 2021-06-16T17:48:28.390Z
tags: 
editor: markdown
dateCreated: 2021-06-16T17:48:28.390Z
---

In order to estimate a web server performance, you can use Apache HTTP server benchmarking tool.

For bench marking the apache you can use the tool ab.The syntax for using the tool is as follows.

```
$ ab -n 10 -c 2 http://www.domain.com/test.html

 -n:  specifies the number of request that is to be sent to the apache server for the bench marking session.
 -c: specifies the number of multiple requests to perform at a time to the server.
```

The below is a sample output.

```
$ ab -n 10 -c 2 http://192.168.1.228/test.html
This is ApacheBench, Version 2.0.40-dev <$Revision: 1.146 $> apache-2.0
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Copyright 2006 The Apache Software Foundation, http://www.apache.org/

Benchmarking 192.168.1.228 (be patient).....done


Server Software:        Apache/2.0.52
Server Hostname:        192.168.1.228
Server Port:            80

Document Path:          /test.html
Document Length:        5 bytes

Concurrency Level:      2
Time taken for tests:   0.375607 seconds
Complete requests:      10
Failed requests:        0
Write errors:           0
Total transferred:      2660 bytes
HTML transferred:       50 bytes
Requests per second:    26.62 [#/sec] (mean)
Time per request:       75.121 [ms] (mean)
Time per request:       37.561 [ms] (mean, across all concurrent requests)
Transfer rate:          5.32 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0   25  54.6      0     130
Processing:     1   48  94.8      2     229
Waiting:        1   48  94.7      2     228
Total:          1   74 149.4      2     358

Percentage of the requests served within a certain time (ms)
  50%      2
  66%     10
  75%     10
  80%    358
  90%    358
  95%    358
  98%    358
  99%    358
 100%    358 (longest request)
```

