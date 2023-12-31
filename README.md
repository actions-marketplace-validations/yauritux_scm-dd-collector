# SCM-DD-COLLECTOR

This is a simple GH custom action that is doing pretty simple job to fetch some code metrics reported by Sonarqube and publish it accordingly to Datadog.

## Inputs

### `sonar-base-url`

**Required** Sonarqube Base URL.

### `datadog-base-url`

**Required** Datadog Base URL.

### `component-name`

**Required** The component name (could be a project name or a service name).

### `metric-names`

**Required** List of code metric names separated by comma (if more than one metric).
More reading on Sonarqube metrics can be read from [here](https://docs.sonarsource.com/sonarqube/latest/user-guide/metric-definitions/).

### `metric-type`

**Required** Type of metric used in report. Only support enum values as following:

-   0 (unspecified)
-   1 (count)
-   2 (rate)
-   3 (gauge)

### `metric-unit`

Unit of metric used in report. Check this [link](https://docs.datadoghq.com/metrics/types/).

## Example Usage

```yaml
uses: yauritux/scm-dd-collector@v1.0
with:
    sonar-base-url: ${{ secrets.DD_SONAR_URL }}
    datadog-base-url: ${{ secrets.DD_BASE_URL }}
    component-name: platform-api
    metric-name: coverage,code_smells,vulnerabilities,security_hotspots
    metric-type: 3
    metric-unit: percent
    dd-api-key: ${{ secrets.DD_API_KEY}}
    dd-application-key: ${{ secrets.DD_APPLICATION_KEY }}
```
