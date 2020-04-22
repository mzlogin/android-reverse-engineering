# Android 逆向工程

My notes for android reverse engineering learning.

## 目录

<!-- vim-markdown-toc GFM -->

* [前言](#前言)
* [工具准备](#工具准备)
    * [必备工具](#必备工具)
    * [调试工具](#调试工具)
    * [备用工具](#备用工具)
* [基础知识准备](#基础知识准备)
    * [Smali](#smali)
        * [数据类型](#数据类型)

<!-- vim-markdown-toc -->

## 前言

一直想写点关于 Android 逆向工程的东西，却迟迟不能开始。先挖个坑放在这里吧，有现成的坑才更容易产生填的欲望。

我要写的不是一份全面且详细的工具介绍，也不是一份完整的技术原理说明，重点在记录与分享我在实践过程中的经验。如果我提到某一个工具，将只介绍我所使用到的功能与命令，想了解工具完整的功能与使用方法可以参考工具的官网。

## 工具准备

### 必备工具

本节罗列的是我使用到的工具集。

* [7-zip][]

    好用的压缩/解压缩软件，Apk 文件基于 ZIP 文件格式，有时候我们需要将其直接解压来分析里面的内容。

* [jadx][]

    直接打开 Dex/Apk 文件查看反编译出的 Java 代码，个人觉得输出的代码可读性比 dex2jar 要好。

* [apktool][]

    Android 逆向工程的主要工具之一，用于：
    1. 将 Apk 文件里的可执行文件和资源解包成我们能看懂的格式。
    2. 将解包后的文件重新打包成 Apk。
    3. 将 Apk 里的 dex 文件反编译成调试版的 Smali 文件。

    *注：根据 apktool 官网的声明，反编译成调试版 Smali 文件的功能将在 2.0.3 版被废弃，到 2.1 版完全移除，因为有了 IdeaSmali。*

* [frida][]

    逆向、Hook 等，还没深入研究过。

### 调试工具

* [Android Studio][]

    用于动态调试。

* [smalidea][]

    用于支持 Android Studio 和 IntelliJ IDEA 高亮显示和动态调试 Smali 文件的插件。

* [IDA Pro][]

    最强大的静态逆向分析工具，没有之一。

### 备用工具

* [enjarify][]

    反编译 Dex/Apk 文件。

* [dex2jar][]

    用于将 dex 文件转化成 jar 文件。

* [jd-gui][]

    用于直接打开 jar 文件阅读 Java 代码，支持搜索，还有一定程度上的类间跳转。

* [Smali 语法高亮与 Tag 支持][]

    Vim 里的 Smali 语法支持。

## 基础知识准备

### Smali

我对 Smali 的认识是它是 Android 使用的 Java 虚拟机能理解的一种字节码。

这部分我是看《Android软件安全与逆向分析》一书的「第 3 章 进入 Android Dalvik 虚拟机」入门。

以下链接可作为手册备查：

* [Dalvik opcodes][]
* [Dalvik bytecode][]

#### 数据类型

**基本数据类型**

| Smali 类型 | 对应 Java 类型          |
|------------|-------------------------|
| V          | void - 只能用作返回类型 |
| Z          | boolean                 |
| B          | byte                    |
| S          | short                   |
| C          | char                    |
| I          | int                     |
| J          | long (64 bits)          |
| F          | float                   |
| D          | double (64 bits)        |

**类类型**

表示方法：

```
Lpackage/name/ObjectName;
```

比如 String 的类型表示为：

```
Ljava/lang/String;
```

**数组类型**

表示方法：

```
[I 对应 int[]
[[I 对应 int[][]
[Ljava/lang/String; 表示 String[]
```

[7-zip]: http://www.7-zip.org/
[apktool]: https://github.com/iBotPeaches/Apktool
[dex2jar]: https://github.com/pxb1988/dex2jar
[jd-gui]: https://github.com/java-decompiler/jd-gui
[Android Studio]: https://developer.android.com/sdk/index.html
[IDA Pro]: https://www.hex-rays.com/products/ida/index.shtml
[Smali 语法高亮与 Tag 支持]: http://mazhuang.org/2015/06/23/vim-taglist-smali/
[smalidea]: https://github.com/JesusFreke/smali/wiki/smalidea
[Dalvik opcodes]: http://pallergabor.uw.hu/androidblog/dalvik_opcodes.html
[Dalvik bytecode]: https://source.android.com/devices/tech/dalvik/dalvik-bytecode.html
[jadx]: https://github.com/skylot/jadx
[enjarify]: https://github.com/Storyyeller/enjarify
[frida]: https://github.com/frida/frida
