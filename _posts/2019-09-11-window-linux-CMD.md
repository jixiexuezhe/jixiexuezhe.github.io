## widows 

netstat -ano |findstr "端口号"
taskkill /f /t /im "进程id或者进程名称"


## linux 

netstat -ntulp "端口号"

kill -9 "端口号"
