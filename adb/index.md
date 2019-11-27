adb命令是adb这个程序自带的一些命令；

adb shell则是调用的Android系统（设备的system/bin目录）中的命令。

<!-- more -->

#### 获取设备列表
```
adb devices
```
> 设备状态有3种
> - device：设备正常连接
> - offline：连接出现异常，设备无响应
> - unknown：没有连接设备

#### 结束启动adb服务
```
adb kill-server
adb start-server
```
> 一般在连接出现异常，未正常列出设备时重启服务

#### 安装apk
```
adb install apk路径
```

#### 卸载apk
```
adb uninstall apk包名
```

#### 从设备复制文件到本地
```
adb pull sdcard/test.txt 本地路径
adb pull sdcard/DCIM/Camera/ 本地路径
```

#### 从本地复制文件到设备
```
adb push 本地文件路径 sdcard/
adb push 本地文件路径 sdcard/DCIM/Camera/
```

#### 查看设备日志
```
adb logcat > 本地文件(debug.log)
```

#### 重启手机
```
adb reboot
```

#### 重启到 Recovery 模式
```
adb reboot recovery
```

#### 重启到 Fastboot 模式
```
adb reboot bootloader
```

#### 查看应用列表
```
adb shell pm list packages
adb shell pm list packages -s
adb shell pm list packages -3
```

#### 查看应用安装路径
```
adb shell pm path apk包名
```

#### 清除应用数据
```
adb shell pm clear apk包名
```

#### 启动activity
```
adb shell am start apk包名/第一个Activity完整包路径
```

#### 启动设置
```
adb shell am start com.android.settings/com.android.settings.Settings
```

#### 启动摄像头
```
adb shell am start -a android.media.action.STILL_IMAGE_CAMERA
```

#### 强制停止应用
```
adb shell am force-stop apk包名
```

#### 删除文件
```
adb shell rm sdcard/test.txt
```

#### 删除文件夹
```
adb shell rmdir sdcard/empty
```

#### 删除文件夹及所有文件
```
adb shell rm -r sdcard/crash
```

#### 触摸事件
```
adb shell input tap 500 500
```
> 点击屏幕上坐标为 500 500 的位置


#### 滑动事件
```
adb shell input swipe 900 500 00 500
```
> 从右往左滑动屏幕

#### 按键
```
adb shell input keyevent 3
```
> number含义
> - 3 HOME键
> - 4 返回键
> - 223 系统休眠
> - 224 点亮屏幕

#### 查看系统属性
```
adb shell getprop
```
> 输出含义
> - ro.build.version.sdk SDK 版本
> - ro.build.version.release Android 系统版本
> - ro.build.version.security_patch Android 安全补丁程序级别
> - ro.product.model 型号
> - ro.product.brand 品牌
> - ro.product.name 设备名
> - ro.product.board 处理器型号
> - ro.product.cpu.abilist CPU 支持的 abi 列表
> - persist.sys.isUsbOtgEnabled 是否支持 OTG
> - dalvik.vm.heapsize 每个应用程序的内存上限
> - ro.sf.lcd_density 屏幕密度

#### 查看设备属性
```
adb shell cat /system/build.prop
```

#### 查看cpu信息
```
adb shell cat /proc/cpuinfo
```

#### 查看系统负载
```
adb shell cat /proc/loadavg
```

#### 查看内存信息
```
adb shell cat /proc/meminfo
```

#### 查看cpu时间片
```
adb shell cat /proc/stat
```
> cpu指标：user, nice, system, idle, iowait, irq, softirq
> - user 用户态时间
> - nice 用户态时间(低优先级，nice>0)
> - system 内核态时间
> - idle 空闲时间
> - iowait I/O等待时间
> - irq 硬中断
> - softirq 软中断
> - intr：系统启动以来的所有interrupts的次数情况
> - ctxt: 系统上下文切换次数
> - btime：启动时长(单位:秒)，从Epoch(即970零时)开始到系统启动所经过的时长，每次启动会改变。
> - processes：系统启动后所创建过的进程数量。当短时间该值特别大，系统可能出现异常
> - procs_running：处于Runnable状态的进程个数
> - procs_blocked：处于等待I/O完成的进程个数

#### 获取内核版本
```
adb shell cat /proc/version
```

#### 查看mac地址
```
adb shell cat /sys/class/net/wlan0/address
```

#### 查看android_id
```
adb shell settings get secure android_id
```

#### 查看ip地址
```
adb shell ifconfig
adb shell ifconfig wlan0
```

#### 查看屏幕密度
```
adb shell wm density
```

#### 查看设备分辨率
```
adb shell wm size
```

#### 设置设备分辨率
```
adb shell wm size 920x480
adb shell wm size 480x920
```

#### 设置显示区域
```
adb shell wm overscan 0,200,0,200
adb shell wm overscan reset
```

#### 截屏
```
adb shell screencap -p /sdcard/screen.png
adb exec-out screencap -p > screen.png
```

#### 录屏
```
adb shell screenrecord /sdcard/screen.mp4
```

#### 查看应用详细信息
```
adb shell dumpsys package apk包名
```

#### 显示当前手机窗口上的App包名和Activity名称
```
adb shell dumpsys activity | grep "mResumedActivity"
```

#### 获取系统中 Acitivty 的详细信息
```
adb shell dumpsys activity
```

#### 获取交互 Activity 的详细信息
```
adb shell dumpsys activity top
```

#### 显示当前任务栈详细信息
```
adb shell dumpsys activity activities
```

#### 查看cpu信息
```
adb shell dumpsys cpuinfo
```

#### 查看内存信息
```
adb shell dumpsys meminfo
```

#### 查看帧率信息
```
adb shell dumpsys gfxinfo
```

#### 查看显示屏信息
```
adb shell dumpsys display
```

#### 查看电源信息
```
adb shell dumpsys power
```

#### 查看电池状态信息
```
adb shell dumpsys batterystats
```

#### 查看电池信息
```
adb shell dumpsys battery
```

#### 查看闹钟信息
```
adb shell dumpsys alarm
```

#### 查看位置信息
```
adb shell dumpsys location
```

#### 查看进程列表
```
adb shell ps
```
> 各列参数：
> - USER 进程当前用户
> - PID Process Id 当前进程id
> - PPID Process Parent Id 父进程ID
> - VSIZE Virtual Size 虚拟内存大小
> - RSS Resident Set Size 实际驻留内存大小
> - WCHAN 休眠进程在内核中的地址
> - PC program counter 下一个指令地址
> - NAME 进程状态值及名称

#### 查看实时资源占用情况
```
adb shell top
```
> 命令参数：
> - -m num 最多显示多少个进程
> - -n num 刷新次数
> - -d num 刷新间隔时间（默认5秒）
> - -s col 按哪列(cpu,vss,rss,thr)排序
> - -t 显示线程信息而不是进程
> - -h 显示帮助文档

> 第一组数据含义
> - User 处于用户态的运行时间，不包含优先值为负进程
> - Nice 优先值为负的进程所占用的CPU时间
> - Sys 处于核心态的运行时间
> - Idle 除IO等待时间以外的其它等待时间
> - IOW IO等待时间
> - IRQ 硬中断时间
> - SIRQ 软中断时间

> 第二组数据的含义
> - PID 进程id
> - PR 优先级
> - CPU% 当前瞬时CPU占用率
> - S 进程状态:D=不可中断的睡眠状态, R=运行, S=睡眠, T=跟踪/停止, Z=僵尸进程
> - THR 程序当前所用的线程数
> - VSS 虚拟耗用内存（包含共享库占用的内存）
> - RSS 实际使用物理内存（包含共享库占用的内存）
> - PCY 调度策略优先级，SP_BACKGROUND/SP_FOREGROUND
> - UID 进程所有者的用户id
> - Name 进程的名称

#### 查看所有进程内存占用情况
```
adb shell procrank -r
```
> 输出参数说明
> - VSS - Virtual Set Size 虚拟耗用内存（包括共享库占用的内存）
> - RSS - Resident Set Size 实际使用物理内存（包括共享库占用的内存）
> - PSS - Proportional Set Size 实际使用的物理内存（比例分配共享库占用的内存）
> - USS - Unique Set Size 进程独自占用的物理内存（不包括共享库占用的内存）

root
#### 发送系统广播
```
adb root
am broadcast -a android.intent.action.BOOT_COMPLETED
```
> 广播说明
> - android.net.conn.CONNECTIVITY_CHANGE 网络连接发生变化
> - android.intent.action.SCREEN_ON 屏幕点亮
> - android.intent.action.SCREEN_OFF 屏幕熄灭
> - android.intent.action.BATTERY_LOW 电量低，会弹出电量低提示框
> - android.intent.action.BATTERY_OKAY 电量恢复了
> - android.intent.action.BOOT_COMPLETED 设备启动完毕
> - android.intent.action.DEVICE_STORAGE_LOW 存储空间过低
> - android.intent.action.DEVICE_STORAGE_OK 存储空间恢复
> - android.intent.action.PACKAGE_ADDED 安装了新的应用
> - android.net.wifi.STATE_CHANGE WiFi 连接状态发生变化
> - android.net.wifi.WIFI_STATE_CHANGED WiFi 状态变为启用/关闭/正在启动/正在关闭/未知
> - android.intent.action.BATTERY_CHANGED 电池电量发生变化
> - android.intent.action.INPUT_METHOD_CHANGED 系统输入法发生变化
> - android.intent.action.ACTION_POWER_CONNECTED 外部电源连接
> - android.intent.action.ACTION_POWER_DISCONNECTED 外部电源断开连接
> - android.intent.action.DREAMING_STARTED 系统开始休眠
> - android.intent.action.DREAMING_STOPPED 系统停止休眠
> - android.intent.action.WALLPAPER_CHANGED 壁纸发生变化
> - android.intent.action.HEADSET_PLUG 插入耳机
> - android.intent.action.MEDIA_UNMOUNTED 卸载外部介质
> - android.intent.action.MEDIA_MOUNTED 挂载外部介质
> - android.os.action.POWER_SAVE_MODE_CHANGED 省电模式开启

#### 设置系统日期和时间
```
adb root
date -s 20160823.3500
```
> 表示将系统日期和时间更改为 2016 年 08 月 23 日 3 点 5 分 00 秒。

#### 开启关闭wifi
```
adb root
adb shell svc wifi enable

adb root
adb shell svc wifi disable
```

#### 查看连接过的wifi密码
```
adb root
cat /data/misc/wifi/*.conf
```
> ssid 即为我们在WLAN设置里看到的名称， psk 为密码， key_mgmt 为安全加密方式。

#### 启用/禁用 SELinux
```
adb root
adb shell setenforce 

adb root
adb shell setenforce 0
```
> SeLinux 是 linux 下的增强安全体系，有三种模式
> - Enforcing 强制打开，拒绝违反安全策略
> - Permissive 遇到违反安全策略仍正常执行，但输出警告
> - Disable 关闭安全策略