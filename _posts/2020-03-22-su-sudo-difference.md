## su，sudo區別

- #### su是個切換用戶的命令，經常用於將普通用戶切換到超級用戶下。舉例：通過普通用戶登錄系統，然後再通過su命令切換到超級用戶下，執行一些需要超級權限的工作，然而這種做法必須把超級用戶的密碼交出來。

```
[david@Web01 ~]$ su
Password:
[root@Web01 david]#
```



- #### sudo允許系統管理員分配給普通用戶一些合理的權力，並且不需要普通用戶知道超級用戶的密碼。因此sudo也被稱為受限制的su，另外sudo也是需要事先進行授權認證，被稱為授權認證的su。

```
### 在root用戶下執行 ###
visudo

###	添加下列參數 ###
david	ALL=(ALL)	NOPASSWD:ALL
```

```
### 使用david普通用戶登入 ###
[david@Web01 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for david:
Last login: Sun Mar 22 16:32:58 CST 2020 on pts/1
[root@Web01 ~]#

```





