```splunk-spl
index=strava type=Run
| timechart span=1w sum(total_elevation_gain) as elevation
```
<img width="1223" height="204" alt="viz_elevation_gain_weekly" src="https://github.com/user-attachments/assets/62df8395-9aa6-414e-859b-fa65b6a90f33" />
