# TrueSight Spark Plugin

A TrueSight Meter plugin that collects metrics from the Spark MetricsServlet sink.

### Prerequisites

|     OS    | Linux | Windows | SmartOS | OS X |
|:----------|:-----:|:-------:|:-------:|:----:|
| Supported |   v   |    -    |    -    |  -   |

This plugin is compatible with Spark 1.2.1 or later.

#### TrueSight Meter versions v4.2 or later

- To install new meter go to Settings->Installation or [see instructions](https://help.boundary.com/hc/en-us/sections/200634331-Installation). 
- To upgrade the meter to the latest version - [see instructions](https://help.boundary.com/hc/en-us/articles/201573102-Upgrading-the-Boundary-Meter).

### Plugin Setup

#### MetricsServlet
MetricsServlet is added by default as a sink in master, worker and client driver.
See the /etc/conf/metrics.properties file on your Spark installation for more details.

#### JMV Source

You can also enable the *jvm source* for instance master, worker, driver and executor to get detailed metrics of the JVM uncommenting the following lines in your /etc/conf/metrics.properties

The plugin gathers metrics from the Master and an optional running application. So you need to configure the host and port for the WebUI of the master and application process.

#### WebUI Configuration

By default, the WebUI for the master runs on port 18080 and, for applications the its on 4040 port. These are the default values for this parameters but you can change them based on your configuration.

### Plugin Configuration Fields

|  Property   | Description |
|:-----------:|:---------------|
| Host | Host of the metrics endpoint on the WebUI for Master or Application. |
| Port | Port of the metrics endpoint on the WebUI for Master or Application. |
| Instance Type | Type of the instance to monitor. It can be Application or Master.| 
| Poll Time (ms) | How often to poll for metrics in milliseconds | 
| Source | The source to display in the legend for this instance|
| Debug Level | If enabled it will show additional debug output in the Plugin Console. |

### Metrics Collected

| Metric Name | Description | Context |
|:------------|:------------|:--------|
| SPARK_MASTER_ALIVE_WORKERS_COUNT | The number of alive workers on master. | Master |
| SPARK_MASTER_WORKERS_COUNT | The number of active workers on the master. | Master |
| SPARK_MASTER_APPLICATIONS_RUNNING_COUNT | Running application count on the master. | Master|
| SPARK_MASTER_APPLICATIONS_WAITING_COUNT | Waiting application count on the master. | Master |
| SPARK_MASTER_NO_APPLICATIONS_RUNNING | Value 1 when applications waiting and none of them are running, 0 otherwise. | Master |
| SPARK_MASTER_JVM_MEMORY_USED | Memory used by the JVM on the master. | Master |
| SPARK_MASTER_JVM_MEMORY_COMMITTED | Memory committed by the JVM on the master. | Master |
| SPARK_MASTER_JVM_HEAP_MEMORY_USED | Heap memory used by the JVM on the master. | Master |
| SPARK_MASTER_JVM_HEAP_MEMORY_USAGE | Percentage of heap memory used by the JVM on the master. | Master |
| SPARK_MASTER_JVM_NONHEAP_MEMORY_COMMITTED | Non-heap memory committed by the JVM on the master. | Master |
| SPARK_MASTER_JVM_NONHEAP_MEMORY_USED | Non-heap memory used by the JVM on the master. | Master |
| SPARK_MASTER_JVM_NONHEAP_MEMORY_USAGE | Percentage of non-heap memory usage by the JVM on the master. | Master |
| SPARK_MASTER_ACTIVE_DRIVERS | Active drivers running. | Master |
| SPARK_APP_JOBS_ACTIVE | Jobs running on the application | App |
| SPARK_APP_JOBS_ALL | All jobs created by the application. | App |
| SPARK_APP_STAGES_FAILED | Failed stages for the application. | App |
| SPARK_APP_STAGES_RUNNING | Running stages for the application. | App |
| SPARK_APP_STAGES_WAITING | Waiting stages for the application. | App |
| SPARK_APP_BLKMGR_DISK_SPACE_USED | Block manager disk space used | App |
| SPARK_APP_BLKMGR_MEMORY_USED | Block manager memory used | App |
| SPARK_APP_BLKMGR_MEMORY_FREE | Block manager remaining memory | App |
| SPARK_APP_JVM_MEMORY_COMMITTED | Memory committed by the JVM of the app | App |
| SPARK_APP_JVM_MEMORY_USED | Memory used by the JVM of the app | App |
| SPARK_APP_JVM_HEAP_MEMORY_COMMITTED | Heap memory committed by the JVM of the app | App |
| SPARK_APP_JVM_HEAP_MEMORY_USED | Heap memory used by the JVM of the app | App |
| SPARK_APP_JVM_HEAP_MEMORY_USAGE | Percentage of heap memory in use by the JVM of the app | App |
| SPARK_APP_JVM_NOHEAP_MEMORY_COMMITTED | Non-heap memory committed by the JVM of the app | App |
| SPARK_APP_JVM_NONHEAP_MEMORY_USED | Non-heap memory used by the JVM of the app | App |
| SPARK_APP_JVM_NONHEAP_MEMORY_USAGE | Percentage of non-heap memory in use by the JVM of the app | App |

### Dashboards

- Spark Master
- Spark Application

### References

http://spark.apache.org/docs/1.2.1/monitoring.html

