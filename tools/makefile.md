[TOC]

# makefile 手册

对于不是单文件而是多文件的c/cpp项目，使用makefile进行编译运行。

## 在终端中使用命令行调用编译器

### 一个简单的项目：

--- main.c

```c
#include"print1.h"
#include"print2.h"

int main()
{
    Print1();
    Print2();
    return 0;
}
```



---print1.c

```c
#include"print1.h"

void Print1()
{
    printf("1\n");
}
```



---print1.h

```c
#include<stdio.h>

void Print1();
```

---print2.c

```c
#include"print2.h"

void Print2()
{
    printf("2\n");
}
```

---print2.h

```c
#include<stdio.h>

void Print2();
```

### 一起编译

在终端中如何调用gcc编译器来编译呢？

```gcc main.c print1.c print2.c -o main```

```gcc -o main main.c print1.c print2.c -I.```

<font color="red"> 在VSCode中，在最后编译前，注意每一个文件需要保存，否则会报错！</font>

### 单独编译

如果说文件很多，每一次修改某一个文件，当整体编译的时候就会浪费时间，将每一修改过的文件也重新编译了。这时候我们单独编译修改过的文件，最后在link，会比较省时间。

```c
gcc main.c -c
gcc print1.c -c
gcc print2.c -c
gcc main.o print1.o print2.o -o main
// 最后一行可以写成
// gcc *.o -o main
```

当然这样也会有某些问题：

一行一行手动输入命令比较麻烦！

这时，我们使用makefile脚本文件来简化。



## makefile

### version 1

```makefile
main : main.c print1.c print2.c
	gcc -o hello main.c print1.c print2.c
```

### version 2

```makefile
# 定义变量
CXX = gcc
TARGET = main
OBJ = main.o print1.o print2.o

# 变量的使用方法
$(TARGET) : $(OBJ)
	$(CXX) -o $(TARGET) $(OBJ)

main.o: main.c
	$(CXX) -c main.c
	
print1.o: print1.c
	$(CXX) -c print1.c
    
print2.o: print2.c
	$(CXX) -c print2.c
```

### version 3

```makefile
CXX = gcc
TARGET = main
OBJ = main.o print1.o print2.o

CXXFLAGS = -c -Wall

# $@表达了：前面的部分
# $^表达了：后面的全部
$(TARGET) : $(OBJ)
	$(CXX) -o $@ $^

# $<表达了：后面的第一个
# 这里的-o由于前面-c的限制，仅仅表达后面是生成的目标文件，而非可执行文件
%.o: %.c
	$(CXX) $(CXXFLAGS) $< -o $@

.PHONY: clean
clean:
	rm -f *.o $(TARGET)
```





在终端中输入make命令：

```
mingw32-make -f makefile
```

1. 我电脑里面加入到环境变量中的是mingw32-make.exe，所以这样写
2. 它会自动检查在当前目录下是否有makefile文件，也可以像我这样指定是哪一个文件

