# Release Notes

## New Features

*  External Workflow Actions
*  Support for external event ids
*  Alert Status Customization
*  Quick Assign
*  Ability to index alert results instead of writing to KV Store
*  Auto resolve informational events

## Enhancements

*  Search Head Cluster support
*  Removed custom alert index / indexes.conf. Default to main index with ability to customize
*  Changed permission style from capabilities to roles to comply with certification requirements
*  Internal: New Splunkd-style REST endpoints because of deprecated Splunk Web endpoints
*  Improved Alert History
*  Reduced Alert Metadata footprint
*  Added alert_manager_user role with read-only permissions to knowledge objects
*  display_fields in Incident Settings is now optional
*  Added a check to the incident edit modal to wait for the owner and status dropdown to be ready before save button gets active


## Changes by Release

- **v2.1.4**/   2016-11-07
    - Fixed disabled migration scripts for fresh installations
- **v2.1.3**/   2016-10-21
    - Fixed migration scripts to check KVStore availability
    - Remove local.meta from distribution
- **v2.1.1**/   2016-10-10
    - Support for non-admin users to modify incidents from Incident Posture dashboard
    - Added capability 'am_is_owner' which is required to be an owner of incidents
    - Added new alert_manager_admin, alert_manager_supervisor and alert_manager_user role as preparation for upcoming features
    - Added support for 'AND' or 'OR' combinations in Suppression Rules
    - Added new dynamic owner selection in Custom Alert Action dialog
    - Added auto subsequent resolve option to resolve new incidents from the same title
    - Added loading indicator to incident posture dashboard when expanding incident to show details
    - Improved incident edit dialog to provide better owner search and selection
    - Fixed IncidentContext to support https scheme and custom splunk web port   Enhanced timestamp display in incident history
    - Lot’s of bugfixes, code cleanups, enhancements and sanitizations. See changelog for details
- **v2.0.5**/   2016-04-15
    - App certification release only - no functional changes included!
- **v2.0.4**/   2016-04-15
    - App certification release only - no functional changes included!
- **v2.0.3**/   2016-04-15
    - Fixed wrong file permissions
    - Fixed wrong default notification scheme seed format
    - Added missing appIcon
    - Fixed a bug where e-mail notifications we not sent correctly
    - Fixed a bug where e-mails haven't been displayed correctly on iOS devices
    - Fixed results_link and view_link in notification context
- **v2.0.2**/   2016-04-14
    - Fixed a bug to reenable inline drilldown on Incident Posture again (Splunk 6.4 compatibility)
    - Merged a pull request to properly support SMTP authentication
    - Fixed a bug where an urgency field in results lead into an error
    - Fixed wrong modular alert description
    - Removed legacy scripted alert action
    - Merged pull request for better quotation in incident posture
    - Improved alert filter populating search
    - Fixed a bug where not all built-in users are shown in the incident edit modal
    - Fixed incident posture to refresh single values automatically
- **v2.0.1**/   2016-01-20
    - Fixed localization support
    - Changed alert column in incident settings to read-only
    - Fixed a bug where token syntax in notifications doesn't work
    - Fixed notifications to support multi-valued fields or comma-separated list of recipients
- **v2.0**  /   2015-11-18
    - Changed from scripted alert action to Custom Alert Action framework
    - Added a customizable incident title
    - Added support for extended notification schemes
    - Added support for incident suppression (False positives, maintenance windows...)
    - Added migration script to ingest default data (email templates and notification schemes) as well as migrating old incident settings to Custom Alert Action parameters
    - Added new Splunk v6.3 style single values
    - Added support to dynamically select a template by referencing a token in the notification scheme
    - Added support for multiple dynamic recipients by using multi-valued fields and a token in the notification scheme
    - Added a search command 'modifyincidents' to update an incident trough a search
    - Added a general default email template
    - Changed token reference in e-mail templates to $result.fieldname$ syntax
    - Bugfixes and performance improvements
- **v1.1**  /   2015-03-12
    - Fixed support for per-result alert actions
    - Added support for search results in e-mail templates
    - Enhanced incident details with description form saved search and selectable list of fields
    - Bugfixes
- **v1.0**  /   2015-01-19
    - Major release with e-mail notifications and templates
    - Lots of bugfixes and enhancements
    - Final release for Splunk Apptitude submission


## Changelog
- **2018-03-20** simcen
	- Added a check to prevent built-in Alert Status deletion
- **2018-03-17** simcen
	- Improved External Workflow Actions by adding a pulldown to select the Alert Action
	- Changed namespace for custom splunkd endpoints
	- Fixed a bug where Suppression Rules didn't work on Alert Metadata fields
- **2018-03-14** simcen
	- Changed external workflow action command retrieval to \_key instead title
- **2018-03-12** simcen
	- Renamed ExternalWorkflowActionSettings to ExternalWorkflowActions and moved related helper endpoints to EWA REST Handler
	- Added Alert Status edit view
- **2018-03-11** simcen
	- Changed build system to gradle
- **2018-03-09** simcen
	- Fixed a bug when Email Notifications were not sent anymore (#206)
	- Fixed a bug where Alert Manager was not compatible with Search Head Clustering (#200)
	- Fixed a bug where priority column wasn't colored correctly when value is "informational" (#180)
	- Fixed drilldown for realtime searches and searches which start with a seeding command (#186)
- **2018-03-07** simcen
	- Migrated user_settings REST endpoint (#203)
	- Migrated email_templates REST endpoint (#203)
	- Moved incident_workflow REST endpoint to helpers (#203)
	- Migrated incident_settings REST endpoint  (#203)
	- Migrated externalworkflowaction_settings REST endpoint  (#203)
- **2018-03-06** simcen
	- Finally migrated all helpers to new REST style endpoints
	- Fixed a bug where externalworkflowaction was not executed
- **2018-03-06** my2ndhead
	- Added external reference id feature (#204)
- **2018-02-26** my2ndhead
	- Removed custom drilldown feature
	- Fixed a bug in the datamodel and posture, where comments were not displayed (#182)
	- Added feature to improve logging with log_event helper function (#199)
	- Added more columns to history table
	- Added feature for external workflow action
	- Improved incident_posture to reload tables always when expanding a row.
	- Fixed a bug in incident_posture, to hide Loading text correctly
- **2018-02-26** simcen
	- Cherry-picked a couple of changes from the release branch
  	- Added back new role alert_manager_user for read-only access to Splunk objects
	- Re-enabled old-fashioned Alert Results drilldown temporarly
- **2018-02-02** simcen
	- Changed user synchronization to check for a role instead of capabilities
	- Removed capabilities as they are not allowed for certification
- **2017-12-18** simcen
	- Added migration script which supports prepopulating empty alert status collection
	- Added a check to the incident edit modal to wait for the owner and status dropdown to be ready before save button gets active (#189)
- **2017-06-25** johnfromthefuture
	- Added support for Conditional Tables in the Incident Posture View (#177)
	- Added support for automatically resolve informational events (#181)
- **2017-05-26** johnfromthefuture
	- Changed checking if "incident created" notification needs to be fired (#178)
- **2017-04-22** johnfromthefuture
	- Changed incident posture with cosmetic enhancements (#177)
	- Changed Incident setting display_fields to be now optional (#177)
- **2017-03-28** johnfromthefuture
	- Added support to index data results from a given alert (#143)
- **2017-03-03** johnfromthefuture
	- Reduced alert metadata (#173)
- **2017-03-02** johnfromthefuture
	- Added role 'alert_manager_user' to have read-only perms. (#168)
	- Modified the event that is generated when auto_previous_resolved happens. The event will now record the resolving incident (#172)
- **2016-11-04** simon@balz.me
    - Introduced new documentation system (mkdocs + readthedocs.io)
- **2016-10-21** simon@balz.me
    - Fixed migration scripts to check KVStore availability
    - Remove local.meta from distribution
    - Updated jinja2 to the latest version
- **2016-10-20** simon@balz.me
    - Improved helper endpoint and CsvLookup library to output csv data
    - Support for dynamic status parsing in incident posture
    - Fixed a CSS bug which hid an element showing "No results found" message
- **2016-10-19** simon@balz.me
    - Fixed broken pagination in Splunk 6.5
    - Removed inline css and js in setup.xml (Certifiaction requirement)
    - Increased version to 2.1.1
- **2016-10-10** simon@balz.me
    - 2.1.0 release preps
- **2016-10-09** simon@balz.me
    - Added new build system (npm with ant, internal change only)
    - Fixed wrong timestamp format in modifyincidents command
    - Removed deprecated parameters from incident posture dashboard
    - Added dynamic owner selection pulldown to alert action config interface
- **2016-09-19** simon@balz.me
    - Changed Customer Alert Action configuration to support dynamic owner selection
    - Fixed an issue with forward slashes in alert names
    - Fixed unhandled exceptions in scheduler
    - Fixed unhandled exceptions in alert_manager.py
- **2016-06-28** simon@balz.me
    - Changed incident posture single values to show always todays nr of incidents compared to yesterday
- **2016-06-24** simon@balz.me  
    - 10k limit Bugfix in macro
- **2016-06-21** simon@balz.me
    - Enhanced timestamp display in incident history
- **2016-06-19** simon@balz.me      
    - Fixed IncidentContext to support https scheme and custom splunk web port  
- **2016-05-13** simon@balz.me
    - Improved logging supporting a config file
- **2016-05-12** simon@balz.me
    - Added support to auto resolve subsequent incidents
- **2016-05-11** simon@balz.me
    - Added support to choose if all or any suppression rules in a ruleset have to match for a positive suppression
    - Added 'Loading...' indicator when expanding a row in incident posture
    - Added JQuery plugin 'Select2' to provide more comfortable owner selection
    - Updated splunk defaukt admin and user roles to support Alert Manager capabilities
    - Removed legacy HTML incident posture dashboard
- **2016-05-10** simon@balz.me
    - Update NotificationHandler.py and _stringdefs.py (jinja2) to correctly close file handles
- **2016-04-22** simon@balz.me
    - Removed unsued incidentresults custom command
    - Changed deprecated <seed/> tag to <initialValue/> in several views
- **2015-04-20** simon@balz.me
    - Changed attribute 'user' in alert_users to 'name', added migration script
- **2016-04-19** simon@balz.me
    - Added support to create incidents by alerts owned by non-admin users
    - Added sync between Splunk users and alert_users kvstore to support non-admin users changing incident ownership    
    - List only users with a certain capability (am_is_owner)
