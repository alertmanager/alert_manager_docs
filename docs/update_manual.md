# Update Manual

## Before you update

**Important:** This release has changes regarding how indexes are handled. Read carefully!

Previous releases were delivered with a default _indexes.conf_ file. Due to certification reasons this is not allowed anymore.

Before upgrading make sure you have a valid indexes.conf on both the search-head and the indexer pointing to your index that stores the alerts (e.g. _alerts_).

**Important**: Do not put the indexes.conf under alert_manager/default or TA-alert_manager/default, as these settings may be lost after an update.

## Update Procedure

Update the alert_manager on the search head, and TA-alert_manager addon on both the search-head and indexer (if needed).

## After the Update

Configure the index where alerts are stored (e.g. _alerts_) in the Alert Manager's _Global Settings_ view:

![Screenshot](img/im_global_settings.png)

Alternatively, you can also set the index name in local/alert_manager

```ini
[settings]
index = alerts
```