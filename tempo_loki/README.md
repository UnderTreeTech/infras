## Grafana Loki & Tempo

Tempo存储Jaeger上报的trace数据，Loki存储详细日志数据, Grafana统一展示收集的数据

- docker-compose up

- 下载[Promtail](https://github.com/grafana/loki/releases) 并修改promtail.yaml中的配置

启动Promtail `./promtail-darwin-amd64 -config.file=./promtail.yaml`

- 下载[Jaeger](https://github.com/jaegertracing/jaeger/releases)

解压出Jaeger agent并启动 `./jaeger-agent --reporter.grpc.host-port=127.0.0.1:14250`

Promtail及Jaeger agent裸机部署并不在docker中。应用服务将Trace发送给agent，Promtail解析日志并发送给Loki