# C/C++程序调试工具使用文档（gdb/lldb）

## 前言


## 安装

ubuntu
```
sudo apt install gdb
```

macos
```
xcode-select --install
```

## 使用

### 启动程序

无参数启动
```
(gdb) gdb
```
```
(lldb) lldb
```

设置参数
```
(gdb) set args 1 2 3
(gdb) run
```
```
(lldb) settings set target.run-args 1 2 3
(lldb) run
```

or 使用参数启动程序
```
gdb --args a.out 1 2 3
(gdb) run
...
```
```
lldb -- a.out 1 2 3
(lldb) run
...
```

## 设置断点

添加断点
```
(gdb) break test.c:12
```

```
(lldb) breakpoint set --file test.c --line 12
(lldb) br s -f test.c -l 12
(lldb) b test.c:12
```

打印断点信息
```
(gdb) info break
```

```
(lldb) breakpoint list
(lldb) br l
```

删除断点
```
(gdb) delete 1
```
```
(lldb) breakpoint delete 1
(lldb) br del 1
```
临时屏蔽断点
```
(gdb) disable 1
```
```
(lldb) breakpoint disable 1
(lldb) br dis 1
```


取消屏蔽断点
```
(gdb) enable 1
```
```
(lldb) breakpoint enable 1
(lldb) br en 1
```


## 调试程序

步入 step in

```
(gdb) step
(gdb) s
```

```
(lldb) thread step-in
(lldb) step
(lldb) s
```
步过 step over
```
(gdb) next
(gdb) n
```
```
(lldb) thread step-over
(lldb) next
(lldb) n
```

步出 step out
```
(gdb) finish
```

```
(lldb) thread step-out
(lldb) finish
```

## 动态库信息查看
```
(gdb) info sharedlibrary 
```