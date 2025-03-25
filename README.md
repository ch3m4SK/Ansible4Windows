# Ansible4Windows
![Ansible Logo](./images/ansible-1.jpg)

<div align="center">
<h1> Introduction</h1>
</div>

A collection of playbooks for the daily management of windows devices, user creation, software installation and feature management for windows. Here I will store all the playbooks that can be useful for windows.

# Initial Set-Up
There are mainly two ways to use ansible for windows, WinRM and SSH, depending on which one you want to use we will have to perform the following steps on all hosts

## WinRM
Run the following commands in powershell to enable control of the computer through WinRM

```shell
# Powershell as administrator
winrm quickconfig
winrm set winrm/config/service/Auth '@{Basic="true"}'
winrm set winrm/config/service '@{AllowUnencrypted="true"}'

```
Enable WinRM (HTTP - Port 5985)
```shell
New-NetFirewallRule -DisplayName "Allow WinRM HTTP" -Direction Inbound -LocalPort 5985 -Protocol TCP -Action Allow -Profile Any
```

Enable WinRM (HTTPS - Port 5986)
```shell
New-NetFirewallRule -DisplayName "Allow WinRM HTTPS" -Direction Inbound -LocalPort 5986 -Protocol TCP -Action Allow -Profile Any
```


## SSH
