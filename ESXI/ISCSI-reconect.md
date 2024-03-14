ISCSI auf ESXI wird nur beim booten gescant, wenn das LUN ueber eine VM auf dem gleichen Host bereitgestellt wird, 
muss dieser scan nach dem Booten neu gestartet werden.

Befehl:
esxcli storage core adapter rescan --all

Automatisierung ueber cron Job:
cat /var/spool/cron/crontabs/root
cp /var/spool/cron/crontabs/root /var/spool/cron/crontabs/root.old
vi /var/spool/cron/crontabs/root    #Oder ueber WinSCP
    --> @reboot sleep 60 && esxcli storage core adapter rescan --all

vi /etc/rc.local.d/local.sh
#Folgende Zeilen einfuegen
/bin/kill $(cat /var/run/crond.pid)
/bin/echo "1 * * * * esxcli system snmp set -e false" >> /var/spool/cron/crontabs/root
/bin/echo "1 * * * * esxcli system snmp set -e true" >> /var/spool/cron/crontabs/root
/usr/lib/vmware/busybox/bin/busybox crond