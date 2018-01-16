---
tap: "bing-ads"
# version: "1.0"

name: "adgroup_performance_report"
doc-link: https://docs.microsoft.com/en-us/bingads/reporting-service/adgroupperformancereportcolumn#values
singer-schema: 
description: |
  The `ad_group_performance_report` table contains performance data for ad groups, aggregated by day.

  [This is a **Report** table](#replication). See the **Replication** section for information on how data is replicated and loaded for this table.

replication-method: "Append-Only (Incremental)"
attribution-window: true
api-method:
  name:
  doc-link: 

attributes:
  - name: "accountId"
    type: "integer"
    primary-key: true
    description: "The Bing Ads-assigned ID of the account."

  - name: "{{ system-column.report-date-time }}"
    type: "date-time"
    primary-key: true
    description: "The start time of the Stitch replication job that replicated this record."

  - name: "gregorianDate"
    type: "date"
    primary-key: true
    replication-key: true
    description: "The day the record pertains to."

  - name: "Custom Fields"
    description: |
      Columns selected by you. For descriptions of available columns, refer to [Microsoft's documentation](https://docs.microsoft.com/en-us/bingads/reporting-service/adgroupperformancereportcolumn#values){:target="_blank"}.
---