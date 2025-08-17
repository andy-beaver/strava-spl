```splunk-spl
index=strava type=Run
| eval pace=(moving_time/60)/(distance*0.000621371)
| stats min(pace) as best_pace
```
