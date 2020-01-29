## fedora-sway
Ansible playbooks to configure Sway WM on Fedora Workstation

## how to run it
Create an `ini` file with Ansible inventory, e.g. 
```ini
[desktop]
192.168.10.10     ansible_connection=ssh        ansible_user=myawesomeusername
``` 
Create file with variables, e.g. var.yml:
```yml
---
config_d_directory: /home/myawesomeuser/.config/sway/config.d/
config_owner: myawesomeuser
config_group: myawesomeuser
config_file: /home/myawesomeuser/.config/sway/config
```
and run it like this to apply configuration from `sway-desktop.yml` to the `desktop` machine while becoming (`-b`) the root user and asking for the sudo password (`-K`) of `myawesomeusername`:
```
$ ansible-playbook sway-desktop.yml -i private/inventory --extra-vars "@private/vars.yml" -b -K
```

