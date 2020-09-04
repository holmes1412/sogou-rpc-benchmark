# Sogou RPC Benchmark

SogouRPC是基于[C++ Workflow](https://github.com/sogou/workflow)异步调度引擎所开发的RPC系统，目前已在公司内部开源，也会在不久的将来在github开源与大家见面，欢迎持续关注！以下是SogouRPC的benchmark。

* CPU 2-chip/8-core/32-processor Intel(R) Xeon(R) CPU E5-2630 v3 @2.40GHz
* Memory all 128G
* 10 Gigabit Ethernet
* BAIDU brpc-client使用连接池pooled模式

#### 跨机单client→单server在不同并发的QPS
~~~
Client = 1
ClientThread = 64, 128, 256, 512, 1024
RequestSize = 32
Duration = 20s
Server = 1
ServerIOThread = 16
ServerHandlerThread = 16
~~~

![IMG](/images/benchmark2.png)

#### 跨机多client→单server在不同client进程数的QPS
~~~
Client = 1, 2, 4, 8, 16
ClientThread = 32
RequestSize = 32
Duration = 20s
Server = 1
ServerIOThread = 16
ServerHandlerThread = 16
~~~

![IMG](/images/benchmark4.png)

#### 同机单client→单server在不同并发下的QPS
~~~
Client = 1
ClientThread = 1, 2, 4, 8, 16, 32, 64, 128, 256
RequestSize = 1024
Duration = 20s
Server = 1
ServerIOThread = 16
ServerHandlerThread = 16
~~~

![IMG](/images/benchmark3.png)

#### 同机单client→单server在不同请求大小下的QPS
~~~
Client = 1
ClientThread = 100
RequestSize = 16, 32, 64, 128, 256, 512, 1024, 2048, 4096, 8192, 16384, 32768
Duration = 20s
Server = 1
ServerIOThread = 16
ServerHandlerThread = 16
~~~

![IMG](/images/benchmark1.png)

#### 同机单client→单server在固定QPS下的延时CDF
~~~
Client = 1
ClientThread = 50
ClientQPS = 10000
RequestSize = 1024
Duration = 20s
Server = 1
ServerIOThread = 16
ServerHandlerThread = 16
Outiler = 1%
~~~

![IMG](/images/benchmark5.png)

#### 跨机多client→单server在固定QPS下的延时CDF
~~~
Client = 32
ClientThread = 16
ClientQPS = 2500
RequestSize = 512
Duration = 20s
Server = 1
ServerIOThread = 16
ServerHandlerThread = 16
Outiler = 1%
~~~

![IMG](/images/benchmark6.png)

