```splunk-spl
index=strava type=Run
| eval miles=distance*0.000621371
| timechart span=1w sum(miles) as weekly_miles
```
<img width="926" height="324" alt="viz_weekly_milage_barchart" src="https://github.com/user-attachments/assets/a117569b-de2e-443b-a9a5-f59b740e5e0d" />
