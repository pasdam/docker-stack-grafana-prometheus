# Prometheus-Grafana metrics stack

This repo contains a basic setup of a Grafana instance using Prometheus to
publish metrics.

## Setup

Spin up the component with:

```sh
docker-compose up
```

Open [Grafana](http://localhost:3000), and login (the default credentials are
`admin`/`admin`), you will be asked to change the password at the first access,
but for local/test setup is possible to skip that step.

Next step it to add a data source to pull metrics from. Go to
`Settings > Data sources`, and add a new Prometheus one. The only thing to
specify is the url, [http://prometheus:9090](http://prometheus:9090), leave the
rest as default and click on `Save and test`.

At this point it's possible to import Prometheus default dashboards, openind the
newly created data source, and click on the import button on each row in the
`Dashboards` tab.

Last thing to do is to import our example dashboard: for this just import
[dashboard.json](grafana/dashboard.json). Note: if you used a custom name for
the data source, you have to edit the file to update the `datasource` property
of each panel.

## Persistence

Both Grafana and Prometheus data are persisted on the local filesystem, as the
`volumes/data` subfolder of each component is mounted as volume in the compose
file.
