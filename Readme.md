Simple Grafana Dashboard for Spring Actuator Micrometer.
====

![Grafana Dashboard](https://raw.githubusercontent.com/nobusugi246/prometheus-grafana-spring-mac/master/images/MicrometerDashboard.jpeg)

Spring Boot Configuration
----

```gradle
dependencies {
    ...
    compile 'org.springframework.boot:spring-boot-starter-actuator'
    compile 'io.micrometer:micrometer-spring-legacy:1.0.0-rc.9'
    compile 'io.micrometer:micrometer-registry-prometheus:1.0.0-rc.9'  // You should add this line for prometheus.
    ...
```

Prometheus Configuration
----

```yaml
scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: 
        - 'localhost:9090'
  - job_name: 'spring'
    metrics_path: '/prometheus'
    static_configs:
      - targets:
        - 'docker.for.mac.host.internal:8080'
```

Grafana Configuration
----

Import `Java Micrometer Basics.json` to you Grafana Server.
