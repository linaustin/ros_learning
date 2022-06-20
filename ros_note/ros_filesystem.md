# Ros_FileSystem #

***

### `$ rospack find [package_name]` ###
example:
``` 
$ rospack find roscpp
```
return：
YOUR_INSTALL_PATH/share/roscpp 

這段指令會回傳package的路徑

***

### `$ roscd <package-or-stack> [/subdir]` ###
example:
```
$ roscd roscpp
```
目錄會移動到 YOUR_INSTALL_PATH/share/roscpp

這段指令可以透過pakage名稱而不是絕對路徑進行cd

***

### `$ rosls <package-or-stack>[/subdir]` ###
example:
```
$ rosls roscpp_tutorials
```
return:
cmake launch package.xml  srv

這段指令可以透過pakage名稱而不是絕對路徑去ls pakage 中的檔案和目錄

***