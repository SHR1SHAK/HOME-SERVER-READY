# Crontab script for servers to auto shutdown and reboot at given time

This is the working cronjob where it is configured to shutdown at `minute:00` `hour:22 (i.e 10pm)` *this is also the time when this script runs and then counts down to the given seconds.`convert hours to seconds with: 60x60xh` where h is how many hours till the system restarts to. 
There is a process where we can use time but its not compatable with every systems, which is why im using seconds

## use this to check if the clock is synced to the time you are in or your server will not shutdown or restart on given time.
```javascript
timedatectl
```

## check timezone if necessary

```javascript
timedatectl | grep Time
```

## change timezone if necessary

```javascript
timedatectl list-timezones
```
After listing the timezones find your time zone and place it in the blow command
```javascript
timedatectl set-timezone "Asia/Kathmandu"
```

Find the rtcwake with `which rtcwake` and change the vlaue below if different. In most case its same.

```javascript
00 22 * * * root /usr/sbin/rtcwake -u -m off -s 46800
```
