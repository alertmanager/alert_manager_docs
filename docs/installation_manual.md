# Installation Manual

## Before you deploy

1. Download the App (<https://splunkbase.splunk.com/app/2665/>) and the Add-on (<https://splunkbase.splunk.com/app/3365/>) from Splunkbase
2. Check if your Splunk installation meets the prerequisites
3. Decide if you want to use Alert Manager's default index `alerts` or not. Configure this index on the Indexers and Search Heads (as we use the REST API, Splunk needs to know the existence of the index on the Search Head too).

### Deployment

Install the App on the Search Head only. Uninstall any existing instances of TA-alert_manager.

## Deploy the Alert Manager App

### Create an index for Alert Manager

The app requires a dedicated index where events created from the Alert Manager will be stored.
By default, the index `main` is used. It is recommended to use an alternative index (e.g. _alerts_)

To create this index, either use Splunk Web (Settings -> Indexes -> New Index) or add a new stanza in indexes.conf:

```ini
[alerts]
homePath   = $SPLUNK_DB/alerts/db
coldPath   = $SPLUNK_DB/alerts/colddb
thawedPath = $SPLUNK_DB/alerts/thaweddb
disabled = false
```

**Important:** Be sure to create the index on all Indexers and Search Heads (the Rest API requires the index to know on Search Heads too).

If you decide to not use the index `alerts`, don't forget to adjust the configuration during App configuration.

Also make sure, that the User Role has access to your index and searches trough your custom index by default.

### Install the Alert Manager App

The Alert Manager App contains the core functionality and configurations.

1. Download the latest app from [Splunkbase](https://splunkbase.splunk.com/app/2665/) or through the In-Splunk app browser
2. **Do not restart Splunk yet!**
3. If you downloaded the app manually from the Splunkbase, upload it to your Splunk server and unpack the archive at `$SPLUNK_HOME/etc/apps`
4. Make sure, the folder name is called `alert_manager
5. Restart Splunk, if it hasn't been restarted yet

### Configure App settings

There are two ways to configure basic App settings:

* Through the App settings page
* With `alert_manager.conf`

We recommend to use the App settings page, as there will be a configuration validation. To use the App settings page, restart Splunk after you've installed the App and open the App. If you open the App the first time, the settings page will show up automatically.

**Notes:**

* Change the index according to your decision whether to use the default one (named alerts) or your custom index. Either change it in the Alert Manager's setup page or in `alert_manager.conf`
* Have a look at `$SPLUNK_HOME/etc/apps/alert_manager/README/alert_manager.conf.spec` for full configuration reference
* Set `is_configured` to the value "1" (without quotes) in `$SPLUNK_HOME/etc/apps/alert_manager/local/app.conf` inside the `[install]` stanza to hide the App's setup page in case you configured the App with the config file
