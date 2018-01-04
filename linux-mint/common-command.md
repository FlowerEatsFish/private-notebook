#### 保持雙系統 (Linux & Windows) 時間一致

```linux
$ timedatectl set-local-rtc 0
```

#### Installing source codes:

1. 配置

   ```linux
   $ ./configure
   ```

   建議：

   ```linux
   $ ./configure --prefix=/usr/local/[package name]
   ```

   如果不使用 --prefix 時，默認設置：

   ```linux
   # 可執行文件 /usr/local/bin
   # 函式庫文件 /usr/local/lib
   # 配置文件 /usr/local/etc
   # 其它資源文件 /usr/local/share
   ```

2. 編譯

   ```linux
   $ make
   ```

3. 安裝

   ```linux
   $ make install
   ```
