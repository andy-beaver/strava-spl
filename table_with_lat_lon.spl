```splunk-spl
index=strava earliest=-1y type=Run has_heartrate=true
| eval run_date = strftime(_time, "%Y-%m-%d")
| eval miles=distance*0.000621371
| eval pace=(moving_time/60)/(distance*0.000621371)
| spath input=_raw path=start_latlng{0} output=lat
| spath input=_raw path=start_latlng{1} output=lng
| eval start_latlng_clean = lat . ", " . lng
| spath input=_raw path=end_latlng{0} output=lat
| spath input=_raw path=end_latlng{1} output=lng
| eval end_latlng_clean = lat . ", " . lng
| rename pace as "avg_pace min/mile"
| table start_date_local, miles, "avg_pace min/mile", average_*, total_elevation_gain, calories, suffer_score, start_latlng_clean, end_latlng_clean
```
