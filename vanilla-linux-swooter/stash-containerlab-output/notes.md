sudo config save -y


admin@sonic:~$ sudo config vlan add 100
admin@sonic:~$ sudo config vlan
Usage: config vlan [OPTIONS] COMMAND [ARGS]...

  VLAN-related configuration tasks

Options:
  -h, -?, --help  Show this message and exit.

Commands:
  add         Add VLAN
  del         Delete VLAN
  dhcp_relay
  member
  proxy_arp   Configure proxy ARP for a VLAN
admin@sonic:~$ config vlan 
add         del         dhcp_relay  member      proxy_arp   
admin@sonic:~$ config vlan an
Root privileges are required for this operation
admin@sonic:~$ show Traceback (most recent call last):
  File "/usr/local/bin/show", line 5, in <module>
    from show.main import cli
  File "/usr/local/lib/python3.11/dist-packages/show/main.py", line 103, in <module>
    routing_stack = get_routing_stack()
                    ^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.11/dist-packages/show/main.py", line 94, in get_routing_stack
    stdout = subprocess.check_output(command, shell=True, text=True, timeout=COMMAND_TIMEOUT)
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/subprocess.py", line 466, in check_output
    return run(*popenargs, stdout=PIPE, timeout=timeout, check=True,
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/subprocess.py", line 550, in run
    stdout, stderr = process.communicate(input, timeout=timeout)
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/subprocess.py", line 1207, in communicate
    stdout, stderr = self._communicate(input, endtime, timeout)
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/subprocess.py", line 2059, in _communicate
    ready = selector.select(timeout)
            ^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/selectors.py", line 415, in select
    fd_event_list = self._selector.poll(timeout)
                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
KeyboardInterrupt
^C
.bash_logout               .bashrc                    .profile                   .sudo_as_admin_successful  
admin@sonic:~$ show vlan

-bash: how: command not found
admin@sonic:~$ show vlaTraceback (most recent call last):
  File "/usr/local/bin/show", line 5, in <module>
    from show.main import cli
  File "/usr/local/lib/python3.11/dist-packages/show/main.py", line 54, in <module>
    from . import muxcable
KeyboardInterrupt
^C^C
admin@sonic:~$ show vlan
Usage: show vlan [OPTIONS] COMMAND [ARGS]...

  Show VLAN information

Options:
  -?, -h, --help  Show this message and exit.

Commands:
  brief   Show all bridge information
  config
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
(failed reverse-i-search)`save': show vlan brief
