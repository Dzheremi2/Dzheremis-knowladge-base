Systemd store its system daemons in  ```/usr/lib/systemd/system/```

To create systemd daemon you should create ```.service``` file inside ```/usr/lib/systemd/system/``` 

This file must be filled like this:

>[!EXAMPLE] .service file content
>
>```
>[UNIT]
>Description = smth
>
>[Service]
>ExecStart = command
>Type = oneshot
>Restart = on-failure
>
>[Install]
>WantedBy = multi-user.target
>```

---
#### How to make your script working for systemd


This conditions must be completed for systemd can initialize your script inside the daemon

- wrong path to script (e.g. /home/py/ReadPressure2AndPostToMqtt.py)
    
- script not executable
    
- no shebang (first line)
    
- wrong path in shebang (e.g. /bin/python3)
    
- internal files in your script might be missing access permissions.
    
- SELinux may be preventing execution of the ExecStart parameter; check /var/log/audit/audit.log for messages of the form: `type=AVC msg=audit([...]): avc: denied { execute }` or in the output of `sudo ausearch -ts recent -m avc -i` 

---
#### What if SElinux blocking my script

To fix SElinux blocking your script permanently, you should use this commands

```shell
sudo semanage fcontext -a -t bin_t '/path/to/script'
sudo restorecon -Fv /path/to/script
```

#### Usefull systemd command for demon debugging

>[!NOTE] Commands
>```shell
> sudo systemctl status daemon.service
>sudo systemctl restart daemon.service
>sudo systemctl enable daemon.service
>sudo systemctl disable daemon.service
>sudo systemctl daemon-reload
>```

---
#### Systemd sets default script's launch preset to disabled

To fix script is disabled by default you should add new parameters to ```/usr/lib/systemd/system-preset/90-default.preset``` 

>[!NOTE] Example
>```
>enable daemon.service
>```
