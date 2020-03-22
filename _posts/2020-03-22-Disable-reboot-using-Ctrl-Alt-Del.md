# 關閉Control-Alt-Delete鍵盤命令

- ### Linux的默認在同時按下Control-Alt-Delete組合建，系統將自動重啟。

```
### Centos 5.x ###
vi /etc/inittab
#ca::ctrlaltdel:/sbin/shutdown -t3 -r now

telinint q

### Centos 6.0 ###
vi /etc/init/control-alt-delete.conf
#exec /sbin/shutdown -r now "Control-Alt-Delete pressed"

### Centos 7.0 ###
ln -sf /dev/null /etc/systemd/system/ctrl-alt-del.target
or
systemctl mask ctrl-alt-del.target

```

