# What is the difference between severity, impact, urgency and priority?
There are many naming standards to classify incidents. The **Alert Manager** follows ITIL framework naming, where priority is calculated from impact and urgency ( impact x urgency = priority ). The impact is taken from the alert settings. The urgency is taken from the incident configuration's default urgency setting, or, if the alert has a field urgency with a valid setting, from the alert's result. For alerts with multiple urgencies, the first urgency level is taken. Urgencies can be overridden manually after an incident has been created.

The incident's priority is calculated with the help of the alert_priority lookup table based on the alert's severity reps. impact and the incident's urgency. The default matrix can be found here.

# How should I understand users?
There are two main reasons why we are using _users_ in our app:

* Incident assignment: Dispatch incident investigation tasks to other colleagues
* Notifications: Receive notifications at different stages by e-mail

# What is the difference between built-in and Alert Manager users?
**Built-in users** are traditional Splunk users. They can be used to re-assign incidents and receive notifications as long as the built-in user repository is activated (see User settings in the Alert Manager).

**Alert Manager users** are *virtual* users configured in the Alert Manager only. The primary usage of these users is to represent user or group accounts outside of Splunk.

* Example 1: You wan't to notify or dispatch an incident to a Domain controller admin when a new Incident has been created, but the admin has no account in Splunk
* Example 2: You wan't to send a notification to a mailing list without having to create a dedicated Splunk user for this purpose.

##  Why do I have to deploy the Add-on on a Search Head?
As the Alert Manager generates some events (by default alerts), they get parsed on the Search Head. So event breaking rules from props.conf need to get applied here, regardless if events get forwarded to indexers later or not.
