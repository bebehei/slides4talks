```
admin@sonic:~$ sudo config vlan add 100
admin@sonic:~$ show vlan config
Name       VID  Member    Mode
-------  -----  --------  ------
Vlan100    100
admin@sonic:~$ show vlan brief
+-----------+--------------+---------+----------------+-------------+-----------------------+
|   VLAN ID | IP Address   | Ports   | Port Tagging   | Proxy ARP   | DHCP Helper Address   |
+===========+==============+=========+================+=============+=======================+
|       100 |              |         |                | disabled    |                       |
+-----------+--------------+---------+----------------+-------------+-----------------------+
admin@sonic:~$ 
```

```
admin@sonic:~$ sudo config save -y
[...]
admin@sonic:~$ cat /etc/sonic/config_db.json
[...]
    },
    "VLAN": {
        "Vlan100": {
            "vlanid": "100"
        }
    }
}
admin@sonic:~$
```


```
$> docker logs clab-sonic-bullshit-sonic
[...]
Value": {"LOGLEVEL": "SAI_LOG_LEVEL_NOTICE", "LOGOUTPUT": "SYSLOG"}}, {"op": "replace", "path": "/DEVICE_METADATA/localhost/mac", "value": "22:2a:c3:68:ef:d8"}]Failed to replace config
Usage: config replace [OPTIONS] TARGET_FILE_PATH
Try "config replace -h" for help.

Error: Given patch will produce invalid config. Error: Data Loading Failed
Value "public" does not satisfy the constraint "Vlan(409[0-5]|40[0-8][0-9]|[1-3][0-9]{3}|[1-9][0-9]{2}|[1-9][0-9]|[2-9])" (range, length, or pattern).

Patch Applier: localhost getting current config db.
Patch Applier: localhost: simulating the target full config after applying the patch.
Patch Applier: localhost: validating all JsonPatch operations are permitted on the specified fields
Patch Applier: localhost: validating target config does not have empty tables,
                            since they do not show up in ConfigDb.
Patch Applier: localhost: sorting patch updates.
Traceback (most recent call last):
  File "/launch.py", line 192, in <module>
    vr.start()
  File "/vrnetlab.py", line 1343, in start
    vm.work()
  File "/vrnetlab.py", line 1171, in work
    self.bootstrap_spin()
  File "/launch.py", line 81, in bootstrap_spin
    self.startup_config()
  File "/launch.py", line 150, in startup_config
    subprocess.run(
  File "/usr/lib/python3.11/subprocess.py", line 571, in run
    raise CalledProcessError(retcode, process.args,
subprocess.CalledProcessError: Command '/backup.sh -u admin -p admin restore' returned non-zero exit status 2.
```
