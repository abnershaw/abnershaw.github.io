# 移除登入系統時的信息

- ### 為了保證系統的安全，可以修改或刪除四個系統文件

```
### 用戶通過本地終端的方式，顯示其文件的內容 ###
/etc/issue				

### 用戶通過ssh或telnet的方式，顯示其文件的內容 默認該文件不會顯示其內容，需再/etc/ssh/sshd_config添加  Banner /etc/issue.net ###
/etc/issue.net	

### 紀錄系統名稱及版本號
/etc/redhat-release	

### 系統公告信息，用戶登入顯示在用戶的終端，管理員用於發布維護資訊 ##
/etc/motd
```

