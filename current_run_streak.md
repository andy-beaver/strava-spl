```splunk-spl
index=strava type="Run" 
| eval run_date = substr(start_date_local, 1, 10) 
| stats count by run_date 
| sort - run_date 
| streamstats current=f window=1 first(run_date) as prev_date 
| eval prev_epoch = strptime(prev_date, "%Y-%m-%d") 
| eval curr_epoch = strptime(run_date, "%Y-%m-%d") 
| eval day_diff = round((prev_epoch - curr_epoch) / 86400) 
| eval streak_break = if(isnull(day_diff) OR day_diff = 1, 0, 1) 
| streamstats sum(streak_break) as streak_id 
| eventstats count as streak_length by streak_id 
| where streak_id = 0 
| stats first(streak_length) as current_streak first(run_date) as latest_run_date
```In case we want a table```
| eval result = "Running Streak: " . current_streak . " days (last run: " . latest_run_date . ")" 
| table result current_streak latest_run_date
```For Single Value in a Dash```
| table current_streak
```
