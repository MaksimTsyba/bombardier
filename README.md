## Installation

```
docker build -t bombardier .
```

## Usage

```
docker run -it bombardier /bin/bash 
```

## Examples
Example of running `bombardier` against [this server](https://godoc.org/github.com/codesenberg/bombardier/cmd/utils/simplebenchserver):
```
> bombardier -c 125 -n 10000000 http://localhost:8080
Bombarding http://localhost:8080 with 10000000 requests using 125 connections
 10000000 / 10000000 [============================================] 100.00% 37s Done!
Statistics        Avg      Stdev        Max
  Reqs/sec    264560.00   10733.06     268434
  Latency      471.00us   522.34us    51.00ms
  HTTP codes:
    1xx - 0, 2xx - 10000000, 3xx - 0, 4xx - 0, 5xx - 0
    others - 0
  Throughput:   292.92MB/s
```
Or, against a realworld server(with latency distribution):
```
> bombardier -c 200 -d 10s -l http://ya.ru
Bombarding http://ya.ru for 10s using 200 connections
[=========================================================================] 10s Done!
Statistics        Avg      Stdev        Max
  Reqs/sec      6607.00     524.56       7109
  Latency       29.86ms     5.36ms   305.02ms
  Latency Distribution
     50%    28.00ms
     75%    32.00ms
     90%    34.00ms
     99%    48.00ms
  HTTP codes:
    1xx - 0, 2xx - 0, 3xx - 66561, 4xx - 0, 5xx - 0
    others - 5
  Errors:
    dialing to the given TCP address timed out - 5
  Throughput:     3.06MB/s
```
