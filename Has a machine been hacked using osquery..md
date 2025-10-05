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