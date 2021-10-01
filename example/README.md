# W03

## 代码工作原理

* 首先通过`SteganographyFactory.java`将**W02**排序算法（例如`QuickSorter.java`）的字节码编码进自选图片`resources/FibonaccciYan.jpeg`，得到隐写术图**example.QuickSorter.png**；
+ 然后运行**Scene**，在这一过程中创建`SteganographyClassLoader`类的实例**loader**，并用上一步得到的图片为其初始化；
+ 接着调用`loader.loadClass()`，加载`example.QuickSorter`类；由于已经提前删去了`QuickSorter.java`文件，因此类加载器无法直接找到`QuickSorter.class`，同时`SteganographyClassLoader.class`中重载了`findClass()`，于是调用该函数，读取**example.QuickSorter.png**并进行解码；
+ 最终，返回解码所得的字节码并赋给`Class c`，由**c**创建实例，从而成功实现了一个可用的**sorter**。

## 隐写术图

1. example.QuickSorter.png:
https://github.com/jwork-2021/jw03-FibonaccciYan/blob/main/example.QuickSorter.png

2. example.HeapSorter.png:
https://github.com/jwork-2021/jw03-FibonaccciYan/blob/main/example.HeapSorter.png

## 排序动画

请见如下链接：
https://www.bilibili.com/video/BV1wP4y187Xq?share_source=copy_web

## 验证