# Cloud Native Observability - 8%
This part of the repository demonstrates the **Cloud Native Observability** part of exam objectives, which covers 8% of the KCNA exam.

---

## Chapter outcomes
At the end of this page you should be able to describe and answer the following questions:
- What's Observability?
- What are Logs, Metrics, and Traces?.
- Which Observability tools are used most in the Cloud Native context?
- What's the relationship between Prometheus and Grafana?
- How can I control my Cloud Native environment costs?

---

## What's Observability?
Observability should give you answers to questions like:
- Is the system stable, or does it change its state when manipulated?
- Is the system sensitive to change, e.g., if some services have high latency?
- Do specific metrics in the system exceed their limits?
- Why does a request to the system fail?
- Are there any bottlenecks in the system?
	
---

### What are Logs, Metrics, and Traces?
- **Logs:**
    - These are messages emitted from an application when errors, warnings, or debug information should be presented.
    - A simple log entry could be the start and end of a specific task that the application performed.
- **Metrics:**
    - Metrics are quantitative measurements taken over time. This could be the number of requests or an error rate.
- **Traces:**
    - Traces track the progression of a request while it’s passing through the system.
    - Traces are used in a distributed system that can provide information about when a service processed a request and how long it took.
    - Traces can be used to understand how a request is processed in a microservice architecture.
    - Traces describe the tracking of a request while it passes through the services.
    - Traces consist of multiple work units representing the different events that occur while the request is passing the system.
    - Each application can contribute a span to the trace, including information like start and finish time, name, tags, or a log message.

---

### Describe how Prometheus can be used to collect and store metrics.
- Prometheus is an open-source tool that collects metrics emitted by applications and servers as time series data - these are very simple data sets that include a timestamp, label, and the measurement itself.
- The Prometheus data model provides four core metrics:
    - **Counter:** a value that increases, like a request or error count
    - **Gauge:** values the increase or decrease, like memory size
    - **Histogram:** a sample of observations, like request duration or response size
    - **Summary**: similar to a histogram, but also provides the total count of observations.
- Applications can expose an HTTP endpoint under `/metrics` instead of implementing it yourself.
- You can use the existing client libraries:
    - Go
    - Java or Scala
    - Python
    - Ruby
- Prometheus has built-in support for k8s and can be configured to automatically discover all services in your cluster and collect the metric data in a defined interval to save them in a time series database.
- To query data that is stored in the time series database, Prometheus provides a querying language called *PromQL*.
- A user can use *PromQL* to select and aggregate data in real time and view it in the built-in Prometheus user interface, which offers a simple graphical or tabular view.
- To visualize Prometheus metrics and all data *Grafana* could be used to build cool and user-friendly dashboards.

---

## How to optimize the Cloud costs?
- Identify wasted and unused resources --> *via good monitoring*
- Right-Sizing --> *via good monitoring*
- Reserved Instances --> *This is a great pricing model if you have a good estimate about the resources you need, maybe even for years in advance*
- Spot Instances --> *If you have a batch job or heavy load for a short time*

---

[Next Part ▶ Quiz](./quiz.md)