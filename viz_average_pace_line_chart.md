```splunk-spl
index=strava type=Run
| eval pace=(moving_time/60)/(distance*0.000621371)
| timechart span=1w avg(pace) as avg_pace
```
<img width="613" height="211" alt="viz_avg_pace_line_chart" src="https://github.com/user-attachments/assets/5af01b07-0880-4712-9b30-1c0f36e90585" />
