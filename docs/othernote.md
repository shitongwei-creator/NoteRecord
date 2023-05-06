### AS 快捷键

##### 工具窗口键盘快捷键
1.版本控制（Git）:alt + 9
2.Logcat :alt + 6
3.隐藏所有工具窗口: ctrl + shift + f12

##### 代码补全
1.代码补全：Ctrl+Shift+Enter
2.快速修复及显示：alt + enter

##### 搜索和导航
1.搜索全部内容（包括代码和菜单）：double click shift
2.查找：ctrl + f
3.查找下一项内容: f3
4.查找上一项内容: shift + f3
5.替换: ctrl + r
6.查找操作： ctrl + shift + r
7.查找类：ctrl + n
8.查找文件：ctrl + shift + n
9.转到上一个编辑位置:ctrl + shift + back
10.查看类的层次结构：ctrl + h

##### 编写代码
1.生成代码（getter、setter、构造函数、hashCode/equals、toString、新文件、新类）:alt + insert
2.查看类的实现方法：ctrl + i
3.展开和收起当前代码：ctrl + 加号/减号
4.复制当前行和选择：ctrl + d
5.添加行注释：ctrl + /
6.添加块注释：ctrl + shift + /
7.基本代码补全：ctrl + blankspace
8.移动到代码初始位置：ctrl + [
9.移动到代码最后位置：ctrl + 

### adb命令

///////////////////////安装/卸载apk
adb install apk路径
adb uninstall apk包名

///////////////////////导入/导出 文件
adb pull remote local
adb push local remote

///////////////////////开启、停止ADB 服务
adb start-server
adb kill-server

///////////////////////使用ADB 命令截屏、录像
adb shell screencap -p 文件保存路径
adb shell screenrecord 文件保存路径
按 Control + C 停止屏幕录制，否则，到三分钟或 --time-limit 设置的时间限制时，录制将自动停止。

///////////////////////调用ActivityManager（am 命令）
adb shell am start -a android.intent.action.VIEW
adb shell am start -n 包名/类名	// adb shell am start -n com.android.settings/.Settings	// adb shell am start com.android.settings
adb shell am startservice 包名/类名
adb shell am boradcast -a 广播Action
adb shell am broadcast -a android.intent.action.BATTERY_CHANGED --ei "level" 3 --ei "scale" 100
--es 表示使用字符串类型参数  --ei 表示int类型参数  --ez 表示boolean类型参数
adb shell force-stop 包名

///////////////////////调用 PackageManager（pm 命令）
adb shell pm uninstall 包名
adb shell pm list packages	// adb shell pm -l
adb shell pm list permission-groups
adb shell pm list features
adb shell pm path 包名	// adb shell pm path com.android.settings
adb shell pm clear 包名	// adb shell pm clear com.android.settings
adb shell pm get-max-users
adb shell pm list users
adb shell pm create-user user_name
adb shell pm remove-user user_id

///////////////////////调用Settings
adb shell settings list system
adb shell settings list global
adb shell settings list secure

adb shell settings put system key value
adb shell settings get system key

///////////////////////dumpsys将系统数据转储到屏幕
adb shell dumpsys package com.android.settings

///////////////////////查看手机系统进程
adb shell top
adb shell ps
adb shell ps | findstr qq  // cmd 下面使用 findstr 命令
adb shell ps | grep qq  // linux下面可直接只用 grep

///////////////////////使用logcat抓 log信息
adb logcat > 1.txt
adb logcat -s 关注log标签
adb logcat -c
adb logcat | grep -iE "xxx|xxx|xxx"

///////////////////////电量管理相关命令
adb shell dumpsys battery unplug
adb shell settings put global low_power 1
adb shell dumpsys battery reset

///////////////////////使用adb 命令进入recovery 模式
adb reboot recovery

///////////////////////logcat 抓取kernel log方法
adb shell logcat -b kernel > kernel.txt

