# microservice-micro
it's a micro service that create by go-micro

go-micro是一个为基于微服务的独立的RPC框架,它是micro toolkit的核心被下面所有的模块使用。下面就是每个独立的个体的特性。

![Image text](images/go-micro.png)

### Registry

registry提供了可插拔的服务自动发现库去寻找当前正在运行的服务, 当前已实现的有consul , etcd, memory和kubernetes, 根据你的喜好接口是很容易实现的。

### Selector

selector通过选择器提供了一个负载均衡机制，当客户端请求一个服务，请求先会为服务去查询registry,这会通常返回一个正在运行的能代表服务的节点，选择器会选择其中一个运行的节点来使用，当有多个请求过来selector允许使用负载算法，当前的算法是轮训和随机哈希和黑名单。

### Broker

broker是发布订阅模式的插件接口。在微服务是一个事件驱动的架构时这里的消息的发布和订阅将是一等公民。当前实现了包括NATS， RABBITMQ , HTTP(用于开发)

### Transport

transport是基于点对点的消息传输的插件接口。当前实现了支持http, rabbitmq , nats, 通过支持这个抽象层 传输可以被无缝的交换。

### Client 

客户端提供了一个创建RPC查询的方式, 它结合了registry, selector, broker, 和transport也提供了重连，超时，使用的上下文等等功能。

### Server

Server是一个创建微服务的接口，提供了一个服务RPC请求的方式。


