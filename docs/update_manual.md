# Update to Release 3.0

## Before you update

**Important:** This release is a Splunk 8.0 or higher release only. Upgrade Splunk to 8.0 first before upgrading!

## Update Procedure

Update the alert_manager on the search head. Remove all instances of TA-alert_manager as it is not needed anymore.

## After the Update

Configure the index where alerts are stored (e.g. _alerts_) in the Alert Manager's _Global Settings_ view:

![Screenshot](img/im_global_settings.png)

Alternatively, you can also set the index name in local/alert_manager

```ini
[settings]
index = alerts
```

See the _Installation Manual_ for more details.