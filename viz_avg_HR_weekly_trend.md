```splunk-spl
index=strava type=Run has_heartrate=true
| timechart span=1w avg(average_heartrate) as avg_hr
```
<img width="424" height="236" alt="viz_avg_HR_weekly_trend" src="https://github.com/user-attachments/assets/78fe655b-dbac-4697-a8a7-ad1702ea6ab7" />
