# gk
bin -binary file location
sbin- system binary location

# to start/stop services
journalctl  <status/start/stop/restart> <serviceName>
systemctl <status/start/stop/restart>  <serviceName>

# to check logs
journalctl -u <SERVICE> -f
systemctl start <service> -l 

# terminal tricks
control + R : reverse search
history #display history of commands
