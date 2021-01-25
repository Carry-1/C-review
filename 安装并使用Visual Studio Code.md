# 安装并使用VS Code编写和运行c和c++程序
首先要知道VS Code只是一个纯文本编辑器，（但它又不是像记事本这样简单的编辑器，它是专用编辑器，可以提供代码高亮（根据特定语言的语法给代码染色，便于阅读）、语法错误检查（在编译前提示错字漏字、不合规的语句等错误）、断点调试、多文件多项目的管理等辅助功能。），不是像Visual C++ 6.0 这样的IDE，不含编译器，所以编译器要自己装好

<font color=red>1.</font>先去VS Code官网下载安装VS Code  
<font color=red>2.</font>下载编译器： MinGW-w64编译器套件。   
&emsp;MinGW-w64中包含gcc.exe和g++.exe，前者用来编译c程序，后者用来编译cpp程序     
&ensp; “安装” 编译器：即配置环境变量    
<font color=red>3.</font> 按照参考文献2.所述一步步配置即可

# 参考文献：
1.[Visual Studio Code 如何编写运行 C、C++ 程序？](https://www.zhihu.com/question/30315894)  

2 [基于 VS Code + MinGW-w64 的C语言/C++简单环境配置,专致小白](https://zhuanlan.zhihu.com/p/77074009)