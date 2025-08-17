```splunk-spl
index=strava type=Run has_heartrate=true
| eval run_date = strftime(_time, "%Y-%m-%d")
| stats avg(average_heartrate) as avg_hr by run_date name
| sort - run_date
| head 30
```
<img width="405" height="221" alt="viz_avg_HR_last30" src="https://github.com/user-attachments/assets/fe99ed11-6abf-4a08-ac8a-e91638f5115c" />
