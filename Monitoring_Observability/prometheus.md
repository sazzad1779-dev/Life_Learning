# Prometheus
### What is Prometheus?
It's a matrics based monitoring system written in go. 
**Functionality:**
1. track and expose metrics
2. collect and store metrics
3. query in the metrics
4. debug, alert, design dashboard


### Prometheus System Architecture
![Prometheus System Architecture](architechture.png)

**How it works?**

Prometheus is a pull based monitoring system over HTTP from a set of system and services (this call taget).

From the target, Prometheus pulls data autometically or Manual exporter and store as Time Series DataBase(TSDB).The term time series refers to the recording of changes over time. 

### **Core Features**
Prometheus's main features are:

- a multi-dimensional **data model** with time series data identified by metric name and key/value pairs
- PromQL, a flexible **query language** to leverage this dimensionality
- no reliance on distributed storage; single server nodes are autonomous
- time series collection happens via a **pull model** over HTTP
- pushing time series is supported via an intermediary gateway
- targets are discovered via **service discovery** or static configuration
- multiple modes of graphing and dashboarding support

[More Information](https://prometheus.io/docs/introduction/overview/)

### Configuration

**Downloading Prometheus**: 
[Download the latest release](https://prometheus.io/download/) of Prometheus for your platform, then extract it:
```bash
tar xvfz prometheus-*.tar.gz
cd prometheus-*
```
The Prometheus server is a single binary called prometheus (or prometheus.exe on Microsoft Windows). We can run the binary and see help on its options by passing the `--help` flag.

```bash
./prometheus --help
usage: prometheus [<flags>]

The Prometheus monitoring server

. . .

```
**Configuring Prometheus**
Prometheus configuration is YAML. The Prometheus download comes with a sample configuration in a file called prometheus.yml that is a good place to get started.
```bash
## prometheus.yml

global:
  scrape_interval:     15s
  evaluation_interval: 15s

rule_files:
  # - "first.rules"
  # - "second.rules"

scrape_configs:
  - job_name: prometheus
    static_configs:
      - targets: ['localhost:9090']
```

There are three blocks of configuration in the example configuration file: `global`, `rule_files`, and `scrape_configs`.

The `global` block controls the Prometheus server's global configuration.
- `scrape_interval`, controls how often Prometheus will scrape targets.
- `evaluation_interval`, controls how often Prometheus will evaluate rules.

The `rule_files` block specifies the location of any rules we want the Prometheus server to load.
- `scrape_configs`, controls what resources Prometheus monitors. 

The `job_name` is a label that is attached to all metrics scraped from this configuration.
- `static_configs` is a list of targets that Prometheus will scrape. Each target is specified by a `targets` key, which is a list of host:port pairs.

Prometheus expects metrics to be available on targets on a path of `/metrics`. So this default job is scraping via the URL:` http://localhost:9090/metrics`.

The time series data returned will detail the state and performance of the Prometheus server.


**To start Prometheus:**
```bash
  ./prometheus --config.file=prometheus.yml
```


Once Prometheus is running, we can access its web UI by navigating to `http://localhost:9090` in a web browser. The web UI provides several features, including:
1. **Graphing**: We can use the "Graph" tab to visualize metrics over time. We can enter PromQL queries to create graphs and analyze the data.
2. **Querying**: The "Query" tab allows us to run PromQL queries to retrieve specific metrics and their values.
3. **Status**: The "Status" tab provides information about the Prometheus server, including its configuration, targets, and rules.
4. **Alerts**: If we have configured alerting rules, the "Alerts" tab will show the current state of alerts. 



### Data model

Prometheus fundamentally stores all data as time series: streams of timestamped values belonging to the same metric and the same set of labeled dimensions.

A time series is identified by a metric name and a set of key-value pairs called labels. For example, consider the following time series:
```bash
# HELP http_requests_total Total number of HTTP requests.
# TYPE http_requests_total counter
http_requests_total{method="POST", handler="/messages"} 1027 1395066363000
```
Here, `http_requests_total` is the metric name. It indicates that the metric is a counter that represents the total number of HTTP requests. The labels `method="POST"` and `handler="/messages"` specify additional dimensions for this metric. This means that we can filter or group this metric by the HTTP method (e.g., POST, GET) and the request handler (e.g., `/messages`, `/users`). The value `1027` is the count of requests at the timestamp `1395066363000`.

**Metric Names**: Metric names convey the general nature of the system being measured. They are typically prefixed with the name of the application or system that the metric belongs to, followed by a descriptive name. For example, `node_cpu_seconds_total` indicates CPU usage from a node exporter.

**Labels**: Labels are key-value pairs that enable Prometheus's multi-dimensional data model. They allow you to filter and aggregate metrics based on these dimensions. For example, `http_requests_total{method="POST", status="200"}` would give you the total number of successful POST requests. Labels are crucial for slicing and dicing your data to gain specific insights.


### Metric types

The Prometheus client libraries offer four core metric types. The Prometheus server does not yet make use of the type information and flattens all data into untyped time series. This may change in the future.

**Counter**: A counter is a cumulative metric that represents a single monotonically increasing counter whose value can only increase or be reset to zero on restart. For example, you can use a counter to represent the number of requests served, tasks completed, or errors.

Do not use a counter to expose a value that can decrease. For example, do not use a counter for the number of currently running processes; instead use a gauge.

**Gauge**: A gauge is a metric that represents a single numerical value that can arbitrarily go up and down. Gauges are typically used for measured values like temperatures or current memory usage, but also "counts" that can go up and down, like the number of concurrent requests.

**Histogram**: A histogram samples observations (usually things like request durations or response sizes) and counts them in configurable buckets. It also provides a sum of all observed values.

**Summary**: Similar to a histogram, a summary samples observations. It also provides a total count of observations and a sum of all observed values. Additionally, it calculates configurable quantiles over a sliding time window.


### Jobs and instances

A job is a logical group of instances with the same purpose, such as a web application or a database. Each instance within a job is identified by its network address (IP or hostname) and port. For example, a job named `webapp` might consist of multiple instances running on different servers or ports.

For example, an API server job with four replicated instances:

**job: api-server**
- instance 1: 1.2.3.4:5670
- instance 2: 1.2.3.4:5671
- instance 3: 5.6.7.8:5670
- instance 4: 5.6.7.8:5671

Automatically generated labels and time series
Prometheus automatically adds several labels to each time series it scrapes. The most important ones are:
- `job`: The job name as defined in the scrape configuration.
- `instance`: The `<host>:<port>` of the scraped target.