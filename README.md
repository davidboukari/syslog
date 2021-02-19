# syslog


## Log to a file & log rotate
* rsyslog
```
ls /etc/rsyslog.d/
20-ufw.conf  21-cloudinit.conf  50-default.conf
vim /var/log/10-iptables.conf
if ( $msg contains 'iptables' )
then {
  /var/log/iptables.log
  stop
}
systemctl restart rsyslog
tail -n 2  /var/log/iptables.log
Feb 19 10:04:08 linuxrtr kernel: [48841.790463] iptables DROP INPUTIN=eth0 OUT=..
```

* logrotate
```
cd /etc/logrotate.d/
ls
alternatives  apache2  apport  apt  bootlog  btmp  conntrackd  dpkg  rsyslog  ubuntu-advantage-tools  ufw  unattended-upgrades  wtmp
cp ufw iptables
vim iptables
cat iptables
/var/log/iptables.log
{
        rotate 7
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog rotate >/dev/null 2>&1 || true
        endscript
}
systemctl restart logrotat
```
