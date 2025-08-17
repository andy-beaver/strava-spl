```splunk-spl
index=strava type=Run has_heartrate=true
| timechart span=1w avg(average_heartrate) as avg_hr
```
<img width="405" height="220" alt="viz_avg_HR_alltime" src="https://github.com/user-attachments/assets/30c39118-4310-45b0-99b3-0992024b8270" />
