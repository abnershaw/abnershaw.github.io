# shell history 紀錄

- ### 通用history命令查看用戶所有的歷史操作，同時shell命令操作紀錄默認保存在用戶目錄下的.bash_history文件中，通作該文件可以查詢shell命令的執行歷史

- ### 默認的histtory命令只能查看用戶歷史操作紀錄，不能區分每個用戶操作命令的時間

- ### 讓history命令自動記錄所有shell的執行時間

```
vi /etc/bashrc

HISTFILESIZE=4000			###定義在.bash_history文件中保存命令的紀錄總數，默認值1000
HISTSIZE=4000				###定義在history命令輸出的紀錄總數
HISTTIMEFORMAT='%F %T '		###定義時間顯示格式，格式與data命令後的" +"%F %T"一樣
export HISTTIMEFORMAT		###作為history的時間變量將值傳遞給history命令

source /etc/bashrc			###使其上述參數生效
```

- ### 驗證

![](https://raw.githubusercontent.com/abnershaw/abnershaw.github.io/master/assets/img/shell/2020-03-28_14-07-19.jpg)

- ### 實現詳細記錄登錄過系統的用戶，IP地址，shell命令，以及詳細操作時間

```
vi /etc/profile

### history
USER_IP=`who -u am i 2>/dev/null | awk '{print $NF}' | sed -e 's/[()]//g'`
HISTDIR=/usr/share/.history
if [ -z $USER_IP ]
then
USER_IP=`hostname`
fi
if [ ! -d $HISTDIR ]
then
mkdir -p $HISTDIR
chmod 777 $HISTDIR
fi
if [ ! -d $HISTDIR/${LONGNAME} ]
then
mkdir -p %HISTDIR/${LONGNAME}
chmod 300 %HISTDIR/${LONGNAME}
fi
export HISTSIZE=4000
DT=`date +%Y%m%d_%H%M%S`
export HISTFILE="$HISTDIR/${LONGNAME}/${USER_IP}.history.$DT"
export HISTTIMEFORMAT="[%Y.%m.%d %H:%M:%S]"
chmod 600 $HISTDIR/${LONGNAME}/*.history* 2>/dev/null

source /etc/profile
```

- ### 驗證

![](https://raw.githubusercontent.com/abnershaw/abnershaw.github.io/master/assets/img/shell/2020-03-28_14-39-28.jpg)

