# lldb调试 指令

- `list`: 看代码

  `list 1`: 从一行

  `list 其他文件名`

  `list 函数名(e.g. main)`

- 设置断点: `breakpoint set --file filename.o --line 10`

  通过别名简化: `command alias bfl breakpiont set -f %1 -l %2`

  查看断点列表: `breakpiont list`

- `bt`: 查看当前所有帧

- `frame variable`: 当前所有变量值

  `frame select`

  `frame info`

- `continue`

- `next`

- `thread backtrace`: 将线程的堆栈打印出来

- `thread return`: 可以接受一个表达式，调用命令之后直接从当前的frame返回表达式的值

- `thread list`: 列出所有的线程

  `thread select`: 选择某个线程

