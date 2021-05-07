# graylog-pipeline-rules
The rules I wrote in Graylog to work on Windows logs.

## Windows LogOn Type Pipeline:
#### Stage 0
event_data_logontype associates a unique numeric ID to a natural language description via .csv file and then puts the natural language description into a new field called _event_data_logon_italiano_
#### Stage 1
logon_type_converter transforms the JSON(?) object (_event_data_logon_italiano_) previously created with the _event_data_logontype_ rule, into a String object. Then puts the string in the _logon_type_converted_ field.
#
## Windows Event ID Pipeline:
#### Stage 0
eventid_windows_rule associates a unique numeric ID to a natural language description via .csv file and then puts the natural language description into a new field called _winlogbeat_winlog_ita_
#### Stage 1
eventid_windows_converter transforms the JSON(?) object ("winlogbeat_winlog_ita") previously created with the _"eventid_windows_rule"_ rule, into a String object. Then puts the string in the _"winlogbeat_winlog_converted"_ field.
#

## Windows Remote IP Pipeline:
#### Stage 0
geo_ip_remip looks for the field "remip" in the message, then uses the Geo IP - MaxMind™ Databases database (downloadable from here: https://dev.maxmind.com/geoip/geoip2/geolite2/) to search the IP location. The rule then creates the fields "remip_geo_location", "remip_geo_country", "remip_geo_city" and associates to them the respective data gathered via lookup table from the Geo IP - MaxMind™ database.

![Capture](https://user-images.githubusercontent.com/23013638/115203946-4252fa80-a0f8-11eb-9867-ff7733426bee.PNG)
