---
title: Ghost Daemon for Start/Stop/Restart Ghost service
description: 
published: true
date: 2021-12-23T16:55:41.067Z
tags: 
editor: markdown
dateCreated: 2021-12-23T16:55:41.067Z
---

# Ghost Daemon for Start/Stop/Restart Ghost service


Ghost do not have a script to start/stop/restart the ghost service. We have to create one manually as per the ghost installation.


> This script will not work if you have more than 1 ghost installation on a server. This script is only for CentOS
{.is-info}


First step is install node PM2 module

```
npm install pm2 -g
```

Now go ahead and create file named in /etc/init.d/ghost with following scripts


```
#!/bin/sh
 
# Source function library.
. /etc/rc.d/init.d/functions
 
# Source networking configuration.
. /etc/sysconfig/network
 
# Check that networking is up.
[ "$NETWORKING" = "no" ] && exit 0
 
exec="/usr/bin/pm2 start index.js --name ghost"
prog="ghost"
user="webroot"
 
[ -e /etc/sysconfig/$prog ] && . /etc/sysconfig/$prog
 
lockfile=/var/lock/subsys/$prog
 
start() {
    #[ -x $exec ] || exit 5
    echo -n $"Starting $prog: "
    # if not running, start it up here, usually something like "daemon $exec"
    export NODE_ENV=production
    cd /var/www/blog/
    daemon --user=$user $exec
    retval=$?
    echo
    [ $retval -eq 0 ] && touch $lockfile
    return $retval
}
 
stop() {
    echo -n $"Stopping $prog: "
    # stop it here, often "killproc $prog"
    pid=`ps -aux | grep -i pm2 | grep $user | grep -v " grep " | awk '{print $2}'`
    kill -9 $pid > /dev/null 2>&1 && echo_success || echo_failure
    retval=$?
    echo
    [ $retval -eq 0 ] && rm -f $lockfile
    return $retval
}
 
restart() {
    stop
    start
}
 
my_status() {
        local base pid lock_file=
 
        base=${1##*/}
 
        # get pid
        pid=`ps -aux | grep -i pm2 | grep $user | grep -v " grep " | awk '{print $2}'`
 
        if [ -z "${lock_file}" ]; then
        lock_file=${base}
        fi
        # See if we have no PID and /var/lock/subsys/${lock_file} exists
        if [[ -z "$pid" && -f /var/lock/subsys/${lock_file} ]]; then
                echo $"${base} dead but subsys locked"
                return 2
        fi
 
        if [ -z "$pid" ]; then
                echo $"${base} is stopped"
                return 3
        fi
 
        if [ -n "$pid" ]; then
                echo $"${base} (pid $pid) is running..."
                return 0
        fi
 
}
 
rh_status() {
    # run checks to determine if the service is running or use generic status
    my_status $prog
}
 
rh_status_q() {
    rh_status >/dev/null 2>&1
}
 
 
 
case "$1" in
    start)
        rh_status_q && exit 0
        $1
        ;;
    stop)
        rh_status_q || exit 0
        $1
        ;;
    restart)
        $1
        ;;
    status)
        rh_status
        ;;
    *)
        echo $"Usage: $0 {start|stop|restart|status}"
        exit 2
esac
exit $?
```

Now set the permission for ghost

```
chmod 755 /etc/init.d/ghost
chkconfig ghost on 
```

Now you can run the following commands

```
service ghost start
service ghost stop
service ghost restart
service ghost status 
```

**Start Ghost on Booting**

**CentOS 7**

Put ghost start command on rc.local and make rc.local executable. 

```
cat >> /etc/rc.d/rc.local <<END
service ghost start
END
chmod 755 /etc/rc.d/rc.local 
```

Thats all.. 

