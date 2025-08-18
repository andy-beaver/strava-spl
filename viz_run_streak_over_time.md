```splunk-spl
index=strava type="Run"
| eval run_date = substr(start_date_local, 1, 10)
| eval _time = strptime(run_date, "%Y-%m-%d")
| timechart span=1d count
| eval count=if(count>=2, 1, count)
```
<img width="1100" height="174" alt="viz_run_streak_over_time" src="https://github.com/user-attachments/assets/1c90c344-3fe0-44df-987d-2bfe04b959cf" />

