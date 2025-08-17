```splunk-spl
index=strava type=Run
| eval mph = average_speed * 2.23694
| stats max(mph) as top_speed
| eval top_speed = round(top_speed, 2)
```
