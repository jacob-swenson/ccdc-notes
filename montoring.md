# monitoring

## List logged in users
` w`

## List pids of logged in bash sessions and kill session
```
ps aux | grep bash
kill -9 <pid>
```

## Logs
```
tail -f /var/log/messages # 
tail -f /var/log/syslog
tail -f /var/log/auth.log
tail -f /home/<user>/.bash_history
```
