# conc-map-bench

conc-map-bench uses the bustle benchmarking harness. This is a port of the well regarded libcuckoo benchmark.

## Workloads

The benchmark measures performance under varying load conditions. This is done
because a map suitable for one workload may not be suitable for another.

### Read Heavy

A read heavy model with few inserts, removals and updates. Models caching of data in places such as webservers and disk page caches.
```
read   98%
insert  1%
remove  1%
update  0%
```

### Exchange

Insert and remove heavy model that replicates a scenario where the map is used to exchange data.
```
read    10%
insert  40%
remove  40%
update  10%
```

### Rapid Grow

An insert heavy model that replicates load in a scenario where the map is used to gather large amounts of data under a short burst.
```
read    5%
insert 80%
remove  5%
update 10%
```

## How to run it?

```sh
mv results results.bk
./scripts/bench.bash
./scripts/plot.bash
```

## Results

Instance: AWS EC2 C7g.8xlarge
OS: Linux 6.2.0-1009-aws

See the `results/` directory.

### Read Heavy (std hasher)
| | |
:-------------------------:|:-------------------------:
![](results/ReadHeavy.std.throughput.svg) | ![](results/ReadHeavy.std.latency.svg)

### Exchange (std hasher)
| | |
:-------------------------:|:-------------------------:
![](results/Exchange.std.throughput.svg) | ![](results/Exchange.std.latency.svg)

### Rapid Grow (std hasher)
| | |
:-------------------------:|:-------------------------:
![](results/RapidGrow.std.throughput.svg) | ![](results/RapidGrow.std.latency.svg)

### Read Heavy (fx hasher)
| | |
:-------------------------:|:-------------------------:
![](results/ReadHeavy.ahash.throughput.svg) | ![](results/ReadHeavy.ahash.latency.svg)

### Exchange (fx hasher)
| | |
:-------------------------:|:-------------------------:
![](results/Exchange.ahash.throughput.svg) | ![](results/Exchange.ahash.latency.svg)

### Rapid Grow (fx hasher)
| | |
:-------------------------:|:-------------------------:
![](results/RapidGrow.ahash.throughput.svg) | ![](results/RapidGrow.ahash.latency.svg)
