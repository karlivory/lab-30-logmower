# Logmower lab

In this example:

* Logmower stack is deployed. Logmower is a homebrew log aggregator
  consisting of
  [log shipping daemon](https://git.k-space.ee/k-space/logmower-shipper-prototype),
  MongoDB for storing log records,
  [log event source](https://git.k-space.ee/k-space/logmower-eventsource) for
  streaming events to browser and a
  [frontend](https://git.k-space.ee/k-space/logmower-frontend)

Tasks:

0. Adjust the hostname for the Ingress rule substituting
   `laurivosandi`
1. Verify that MongoDB cluster starts up and
   `logmower-mongodb-application-readwrite` and
   `logmower-mongodb-application-readonly` secrets are created
2. Verify the shipping daemons start up
3. Verify the frontend and event source start up
4. Verify you can access the frontend
5. Verify Prometheus picks up shipping daemon metrics
6. Add you Prometheus instance as datasource into
   [Grafana](https://grafana.codemowers.eu/datasources/new)
7. Using `logmower_bulk_insertion_count_total` and
   `logmower_record_count_total{stage="commited"}` metrics add timeseries diagram
8. Using `logmower_bulk_submission_message_count_bucket` metric
   add heatmap for bulk insertion size histogram
9. Using `logmower_database_operation_latency_bucket{operation="insert-many"}`
   metric add heatmap for bulk insertion latency histogram

Extra:

* Transplant `Deployment` and `Service` for
  Mongoexpress from
  [lab-11](https://github.com/codemowers/lab-11-mongodb/blob/main/application.yml#L85)
  and using `kubectl port-forward` attempt to access the database contents
