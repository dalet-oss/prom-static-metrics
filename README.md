# prom-static-metrics
This is a simple Prometheus server that exposes the list of static metrics configured with the config file.

## Server Config

Server configured with these env vars:
 - `CONFIG_FILE` - path to the config file
 - `PORT` - server port

## config format

```yaml
metrics:
  - name: release_version # name of the metric
    value: x.y.z # metric value, 
    description: prints release information
  - name: is_some_feature_flag_enabled
    value: true #  could be whatever -> converted to the string
    description: Prints state of the feature flag # metric description
```

As a result, on the `/metrics` of the server the following set of metrics will be available:
```
# HELP is_some_feature_flag_enabled Prints state of the feature flag
# TYPE is_some_feature_flag_enabled gauge
is_some_feature_flag_enabled{value="true"} 1
# HELP release_version prints release information
# TYPE release_version gauge
release_version{value="x.y.z"} 1```