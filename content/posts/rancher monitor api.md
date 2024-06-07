---
categories: [个人笔记]
tags: [个人笔记]
title: rancher monitor api
date: '2022-09-22T08:21:18.055Z'
lastmod: '2024-05-08T11:16:12.779Z'
---

# rancher monitor api

CPU SYSTEM

```
URL/k8s/clusters/${cluster-id}/api/v1/namespaces/cattle-monitoring-system/services/http:rancher-monitoring-grafana:80/proxy/api/datasources/proxy/1/api/v1/query_range?query=(sum(rate(container_cpu_system_seconds_total{namespace=~"${namespace-id}"}[240s])) by (pod) OR sum(rate(windows_container_cpu_usage_seconds_kernelmode{namespace=~"${namespace-id}"}[240s])) by (pod)) * on(pod) kube_pod_info{namespace=~"${namespace-id}", created_by_kind="${type}", created_by_name="${resource-id}"}&start=${time-start}&end=${time-end}&step=${step}
```
