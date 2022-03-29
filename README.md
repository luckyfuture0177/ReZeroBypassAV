## ReZeroBypassAV

记录从零开始写一个免杀项目的过程，学习路线参考[倾旋的恶意代码逃逸系列文章](https://github.com/Rvn0xsy/BadCode)，同时也会加入自己的思考和解决方案。

- [各语言ShellcodeLoader初探](https://luckyfuture.top/ShellcodeLoader.html)
- [从0开始写ShellCode加载器0x1-Windows内存操作api](https://luckyfuture.top/BypassAVLearning.html)
- [从0开始写ShellCode加载器0x2-分离免杀](https://luckyfuture.top/BypassAVLearning2.html)
- [从0开始写ShellCode加载器0x3-C++/C指针详解](https://luckyfuture.top/Cpp&CPointer.html)
- [从0开始写ShellCode加载器0x4-隐藏导入表](https://luckyfuture.top/BypassAVLearning4.html)

### 进度

| 时间      | 所用技术                                                     | 免杀效果                                              |
| --------- | ------------------------------------------------------------ | ----------------------------------------------------- |
| 2022.3.28 | 调用virtualAlloc等api分配内存，创建线程加载，隐藏导入地址表，http远程加载shellcode | 静动过360，火绒，静态过defender virustotal查杀率10/67 |
|           |                                                              |                                                       |
|           |                                                              |                                                       |



### 学习资料

~~~
回调函数
https://github.com/ChaitanyaHaritash/Callback_Shellcode_Injection
https://mp.weixin.qq.com/s/74wDqy_MMaUrve1FRZCqZg python实现
~~~

~~~
go语言加载器
https://mp.weixin.qq.com/s/H4ySyC8-80RX6CS2O-L3jA
https://mp.weixin.qq.com/s/RemNu1gsKc7W_uULk0augg
~~~

~~~
syscall
https://f5.pm/go-105319.html
https://yougar0.github.io/2021/12/03/Hell-s-Gate技术/
~~~

~~~
inceptor
https://mp.weixin.qq.com/s/7MOAcusYlErzA4F_BXnZNw 解析
https://github.com/klezVirus/inceptor#usage 项目地址
~~~

~~~
shellcode处理
[将.NET程序集转换为shellcode](https://mp.weixin.qq.com/s/DoWRTIIBwuvzRd59wIWpXw)
[aes加密shellcode](https://github.com/mai1zhi2/ShellCodeFramework)
https://github.com/hasherezade/pe_to_shellcode
~~~

~~~
DLL注入
[深入理解反射式 dll 注入技术](https://paper.seebug.org/1855/)
https://payloads.online/archivers/2020-01-02/1/ MemoryModule
sRDI反射注入 https://mp.weixin.qq.com/s/GeR1Uc2zmdoHUD1m4PUPkA
~~~



### 待解决问题

动态内存分配

类型转换

### 免杀思路

AES + XOR +魔改base64加密的 shellcode（减小程序熵值）

Shellcode拆分（多端交叉加载）

LSB隐写（远端下载shellcode防止查杀）

APC 进程注入 (从任意父进程执行恶意进程)

随机生成的 AES 密钥和 iv（每次都是新的hash）

资源修改（减小用户怀疑）

内存休眠（避免敏感操作）

Syscall（防止杀软hook敏感api）

动态修改自身（云查杀）

杀免分离（自启+快速下线）

Mainifest（UAC）

二次开发的Cobalt Strike（修复烂大街的特征）

流量加密（对抗流量分析）

内存加密（卡巴斯基内存扫描）

反沙盒（检测内存+硬盘大小+有无U盘插拔记录）

反调试（自己调试自己）

捆绑（增加钓鱼成功率）

CDN（保护C2服务器）
