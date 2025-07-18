
# Huawei SNMP Exporter Modules & Grafana Dashboard

This repository provides custom SNMP modules for Huawei storage systems (such as Dorado) and a Grafana dashboard for visualizing their metrics using [Prometheus SNMP Exporter](https://github.com/prometheus/snmp_exporter).

## Contents

* `snmp_huawei_module.yml` — Edited SNMP modules for Huawei devices
* `grafana_dashboard.json` — Grafana dashboard JSON for Huawei metrics visualization

## How to Use

### 1. Add SNMP Module to `snmp.yml`

To use the SNMP modules with your SNMP exporter, copy the desired module from the `modules/` directory and paste it into your existing `snmp.yml` under the `modules:` section.

**Example:**

```yaml
modules:
  huawei_custom:
    walk:
      - 1.3.6.1.2.1.1
      ...
    metrics:
      - name: sysUpTime
        oid: 1.3.6.1.2.1.1.3.0
        type: gauge
```

> ⚠️ Make sure the indentation and syntax are correct after adding the module.

### 2. Reload SNMP Exporter

After updating `snmp.yml`, restart or reload your SNMP exporter for the changes to take effect.

### 3. Import Grafana Dashboard

Go to Grafana → Dashboards → Import → Upload `dashboard/huawei-grafana.json` or paste the JSON.

You may need to adjust the data source to point to your Prometheus instance.

