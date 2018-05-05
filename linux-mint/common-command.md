# Common commands

## 保持雙系統 (Linux & Windows) 時間一致

```shell
$ timedatectl

#       Local time: Fri 2018-01-05 16:56:34 CST
#   Universal time: Fri 2018-01-05 08:56:34 UTC
#         RTC time: Fri 2018-01-05 08:56:34
#        Time zone: Asia/Taipei (CST, +0800)
#      NTP enabled: yes
# NTP synchronized: yes
#  RTC in local TZ: no
#       DST active: n/a

$ timedatectl set-local-rtc 1

$ timedatectl

#       Local time: Fri 2018-01-05 16:57:29 CST
#   Universal time: Fri 2018-01-05 08:57:29 UTC
#         RTC time: Fri 2018-01-05 16:57:29
#        Time zone: Asia/Taipei (CST, +0800)
#      NTP enabled: yes
# NTP synchronized: yes
#  RTC in local TZ: yes
#       DST active: n/a
#
# Warning: The RTC is configured to maintain time in the local time zone. This
#          mode is not fully supported and will create various problems with time
#          zone changes and daylight saving time adjustments. If at all possible, use
#          RTC in UTC by calling 'timedatectl set-local-rtc 0'.
```

## Installing source codes

```shell
# 1. 配置 (通常)
$ ./configure

# 1. 配置（建議）
$ ./configure --prefix=/usr/local/[package name]
# 如果不使用 --prefix 時，默認設置：
# 可執行文件 /usr/local/bin
# 函式庫文件 /usr/local/lib
# 配置文件 /usr/local/etc
# 其它資源文件 /usr/local/share

# 2. 編譯
$ make

# 3. 安裝
$ make install
```
