
William-Yeh.es_cluster_exporter for Ansible Galaxy
============

[![Circle CI](https://circleci.com/gh/William-Yeh/ansible-es-cluster-exporter.svg?style=shield)](https://circleci.com/gh/William-Yeh/ansible-es-cluster-exporter) [![Build Status](https://travis-ci.org/William-Yeh/ansible-es-cluster-exporter.svg?branch=master)](https://travis-ci.org/William-Yeh/ansible-es-cluster-exporter)



## Summary

Role name in Ansible Galaxy: **[William-Yeh.es_cluster_exporter](https://galaxy.ansible.com/William-Yeh/es_cluster_exporter/)**

This Ansible role has the following features for [es_cluster_exporter](https://github.com/William-Yeh/es_cluster_exporter) (a [Elasticsearch](https://www.elastic.co/products/elasticsearch) cluster metrics exporter for [Prometheus](http://prometheus.io/)):

 - Install specific versions of es_cluster_exporter;
 - Handlers for restart/reload/stop events.

NOTE: If you want to install Prometheus itself or other exporters, see **[williamyeh.prometheus](https://github.com/William-Yeh/ansible-prometheus)** for more info.


## Role Variables


### Mandatory variables

None.


### Optional variables: version

Install specific version of Elasticsearch cluster exporter:

```yaml
# default version
prometheus_es_cluster_exporter_version: 1.2.0
```


### Optional variables: command-line arguments


Additional command-line arguments, if any (use `es_cluster_exporter --help` to see the full list of arguments):

```yaml
prometheus_es_cluster_exporter_opts
```


### Optional variables: use systemd or not

If the Linux distributions are equipped with systemd, this role will use this mechanism accordingly. You can disable this (i.e., use traditional SysV-style init script) by defining the variable to false: `prometheus_es_cluster_exporter_use_systemd: false`.

```yaml
prometheus_es_cluster_exporter_use_systemd
```


### Optional variables: general settings of Prometheus

This section lists all variables common for all Prometheus servers and exporters. You may have seen them in my **[williamyeh.prometheus](https://github.com/William-Yeh/ansible-prometheus)** role.


User-configurable defaults:

```yaml
# user and group
prometheus_user:   prometheus
prometheus_group:  prometheus


# directory for executable files
prometheus_install_path:   /opt/prometheus

# directory for logs
prometheus_log_path:       /var/log/prometheus

# directory for PID files
prometheus_pid_path:       /var/run/prometheus



# version of helper utility "gosu"
gosu_version:  1.10
```



## Handlers

- `restart es_cluster_exporter`

- `reload es_cluster_exporter`

- `stop es_cluster_exporter`


## Usage


### Step 1: add role

Add role name `William-Yeh.es_cluster_exporter` to your playbook file.


### Step 2: add variables

Set vars in your playbook file, if necessary.

Simple example:

```yaml
---
# file: simple-playbook.yml

- hosts: all
  become: True
  roles:
    - William-Yeh.es_cluster_exporter

  vars:

    prometheus_es_cluster_exporter_opts: "-es.timeout=20s -web.listen-address=':9114' "
```



## Dependencies

None.


## License

MIT License. See the [LICENSE file](LICENSE) for details.
