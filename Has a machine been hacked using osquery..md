Download and install osquery.
https://osquery.io/

This acts like most other databases.

To see processes.
```
select distinct p.name, l.port, l.address, p.pid FROM processes p JOIN listening_ports l ON p.pid = l.pid;
```

start up items
```
SELECT source, name, name, path FROM startup_itmes;
```

Other persistent 
```
SELECT name, action, path, enabled, next_run_time FROM scheduled_task;
```

Was it deleted
```
SELECT name, path, pid, FROM processes WHERE on_disk = 0;
```

