process checks:
1. ps aux 
2. top
3. pgrep bash
service checks:
1. systemctl status cron - to check the status of cron sevice
2. systemctl is-enabled cron - o/p : "enabled"   meaning cron service is running in background, it is enabled
log checks: (log is like record of what is happening in the system, it basically helps us understand if theres any error or server crashing we can check the logs to see what is heppening in thr system, helps in debugging too)
1. journalctl -u cron - to check the activities of cron service
2. tail -n 20 /var/sys/log - to check the last 20 lines of the system activities (checks general system issue)

troubleshooting problem:
suppose cron service isnt running, what do we do:
we check the status first, systemctl status cron
then, we check the logs of cron service, journalctl -u cron
there we might find the errors or what is causing the problem, then we might fix it.
