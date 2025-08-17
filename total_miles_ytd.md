```splunk-spl
index=strava type=Run earliest=@y
| eval miles=distance*0.000621371
| stats sum(miles) as total_miles
```
