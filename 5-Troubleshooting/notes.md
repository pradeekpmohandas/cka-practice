# when kubectl dont respond
docker ps -a 
docker logs #to check logs of system components
systemctl status <service-name>
journalctl | grep <service-name> #to check logs of service