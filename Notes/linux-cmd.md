bin -binary file location
sbin- system binary location


journalctl  <status/start/stop/restart> <serviceName>
systemctl <status/start/stop/restart>  <serviceName>

#to check logs
journalctl -u <SERVICE> -f
systemctl start <service> -l 


control + R : reverse search
history #display history of commands
