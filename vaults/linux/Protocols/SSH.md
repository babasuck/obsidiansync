Secure  Shell

Протокол для удаленного доступа по защищенному каналу. Также может тунеллировать TCP трафик.
## Server

Существует несколько реализаций протокола как платных, так и бесплатных.
Самая популряная и бесплатная - `OpenSSH` распространяется под открытой лицензией.
`OpenSSH` - это набор программ-компонентов.
- ssh 
- scp
- sftp
- sshd
- sftp-server
- ssh-keygen
- ssh-keysign
- ssh-ssh-keyscan
- ssh-agent
- ssh-add
### Установка сервера
```shell
sudo apt install openssh-server
sudo systemctl enable sshd
```
### Конфигурация сервера

Настроить сервер можно либо через демон `sshd` либо в файле `/etc/ssh/sshd_config` (предпочтительнее).
При конфигурации через `sshd` значения в файле переписываются.
```shell
sudo nano /etc/ssh/sshd_config
```



## Client

