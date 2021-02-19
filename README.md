# syslog


## rsyslog
```
ls /etc/rsyslog.d/
20-ufw.conf  21-cloudinit.conf  50-default.conf
vim /var/log/10-iptables.conf
if ( $msg contains 'iptables' )
then {
  /var/log/iptables.log
  stop
}
```
