# fluentd-loki
Fluentd -> Loki helm recipe 

1. Download the helm chart

2. Configure the chart. 
  - Resources and limits can be tuned
  - Fluentd config can be changed too and provide a different one
  - Authentication can be setup

| Parameter                       | Description                                | Default                                                    |
| ------------------------------- | ------------------------------------------ | ---------------------------------------------------------- |
| `resources.limits.cpu`          | CPU limit                                  | `100m`                                                     |
| `resources.limits.memory`       | Memory limit                               | `200Mi`                                                    |
| `resources.requests.cpu`        | CPU request                                | `100m`                                                     |
| `resources.requests.memory`     | Memory request                             | `200Mi`                                                    |
| `loki.username`                     | Loki username                      | `nil`                                                |
| `loki.password`                | Loki Password                          | `nil`                                                      |
| `loki.url`            | Loki API Url                      | `nil`                                                      |
| `fluentdConfig`                 | Fluentd configuration                      | `example configuration`                                    |


3. Install the chart
```
helm install --name=fluentd-loki ./ --set loki.username=<LOKI_USERNAME> loki.password=<LOKI_PASSWORD>
```

4. Check logs of fluentd pods. They should display messages like

```
[g8s-fluentd-loki-g2xhn] 2018-02-21 21:58:12 +0000 [info]: stats - namespace_cache_size: 1, pod_cache_size: 3, namespace_cache_api_updates: 3, pod_cache_api_updates: 3, id_cache_miss: 3
```

5. Log should be seen in Grafana Explore with Loki datasource.