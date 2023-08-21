# InfluxDB Cloud Usage Grafana Dashboard

This is a port of the [InfluxDB Cloud Usage Dashboard](https://github.com/influxdata/community-templates/tree/master/usage_dashboard) to Grafana, adding in some cost calculations based on suggestions in [Using the New Flux Usage API to Calculate Pricing for InfluxDB Cloud](https://www.influxdata.com/blog/using-the-new-flux-usage-api-to-calculate-pricing-for-influxdb-cloud/).

It uses the [`experimental/usage`](https://docs.influxdata.com/flux/v0.x/stdlib/experimental/usage/) package to help InfluxDB Cloud users monitor their organisations data usage, whilst providing estimations of billing costs incurred during the queried period.

Because it relies on `experimental/usage` the template is only compatible with the cloud version of InfluxDB 2.

![Screenshot of the top of the dashboard](/screenshots/dash_top.png)


----

### Exposed Metrics

The dashboard visualises the following metrics

* Data in (and cost estimation)
* Data out (and cost estimation)
* Query count (and cost estimation)
* Storage hours (and cost estimation)
* Total cost estimation
* Applied rate limits (read, write and cardinality)
* Rate limit events

----

### Setup

Add your InfluxDB Cloud organisation [to Grafana as a Flux datasource](https://docs.influxdata.com/influxdb/cloud/tools/grafana/?t=Flux).

The token used for this data-source must, at minimum, have the following privileges

* Read - All Buckets
* Read - All Orgs

The latter can be found under `Other Resources` when creating a custom API token

![Location of the All Orgs permission](/screenshots/tokens.png)

Once you have an appropriate datasource, download [influxcloud_usage.json](influxcloud_usage.json) from this repository.

Then

1. Choose Dashboards
1. Click `New`
1. Click `Import`
1. Click to upload JSON
1. Select the downloaded file
1. Choose the InfluxDB datasource detailed above


----

### Dashboard Variables

The dashboard exposes a number of variables used in the costing estimations

* `Data in $/MB`
* `Query cost $/100 queries`
* `Storage $/GB-hour`
* `Data out $/GB`

Up to date pricing can be found at [https://www.influxdata.com/influxdb-pricing/](https://www.influxdata.com/influxdb-pricing/).

