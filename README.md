# android-reverse-engineering

My notes for android reverse engineering learning.

## 目录

* [前言](#前言)
* [工具准备](#工具准备)
    * [我使用的工具](#我使用的工具)
    * [其它工具](#其它工具)
* [基础知识准备](#基础知识准备)
    * [Smali](#smali)

## 前言

一直想写点关于 Android 逆向工程的东西，却迟迟不能开始。先挖个坑放在这里吧，有现成的坑才更容易产生填的欲望。

## 工具准备

### 我使用的工具

本节罗列的是我使用到的工具集。

* [apktool][1]

    A tool for reverse engineering Android apk files

* [dex2jar][2]

    Tools to work with android .dex and java .class files

* [jd-gui][3]

    A standalone Java Decompiler GUI

* [Android Studio][4]

    用于动态调试。

* [IDA Pro][5]

    最强大的静态逆向分析工具，没有之一。

* [Smali 语法高亮与 Tag 支持][6]

    Vim 里的 Smali 语法支持。

### 其它工具

* [smalidea][7]

    用于支持 Android Studio 和 IntelliJ IDEA 高亮显示和动态调试 Smali 文件的插件。

## 基础知识准备

### Smali

这部分我是看《Android软件安全与逆向分析》一书的「第 3 章 进入 Android Dalvik 虚拟机」入门。

以下链接可作为手册备查：

* [Dalvik opcodes][8]
* [Dalvik bytecode][9]

[1]: https://github.com/iBotPeaches/Apktool
[2]: https://github.com/pxb1988/dex2jar
[3]: https://github.com/java-decompiler/jd-gui
[4]: https://developer.android.com/sdk/index.html
[5]: https://www.hex-rays.com/products/ida/index.shtml
[6]: http://mazhuang.org/2015/06/23/vim-taglist-smali/
[7]: https://github.com/JesusFreke/smali/wiki/smalidea
[8]: http://pallergabor.uw.hu/androidblog/dalvik_opcodes.html
[9]: https://source.android.com/devices/tech/dalvik/dalvik-bytecode.html
