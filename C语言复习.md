## 源程序、目标程序、可执行程序的关系
C***源程序***经过编译器（编译程序）编译之后，生成一个后缀名为 **.obj**的二进制文件（称为***目标程序***）最后还要由链接程序把.obj文件与编译系统提供的各种***库函数***链接在一起，生成一个后缀名为 **.exe**的 ***可执行程序***

--- 
C语言的声明部分不是C语句，编译时不产生机器指令，只是对有关数据的声明。

---
以0开头的数为八进制数 比如028

---
如果一个c语言程序存放在多个文件中，那么这多个文件可以通过预编译指令'#include'来相互关联

---
## 枚举类型   
enumration
声明枚举类型的格式如下：  
enum weekday{sun,mon,tue,wed,thu,fri,sat};
编译系统在编译时，自动给sun~sat这7个枚举常量赋值0~6，
程序示例：
```
#include <iostream>
#include <iomanip>   //输出时要用到setw控制符
using namespace std;
int main()
{
	enum color{red,yellow,blue,white,black};   //声明枚举类型color
	color pri;
	int i,j,k,n=0;   //n用于记录不同颜色的排列组合数
	for(i=red; i<=black; i++) //第一个球的颜色
		for(j=red; j<=black; j++)   //第二个球的颜色
			if(i!=j)  //判断第一、二个球的颜色是否相同，不同再判断第三个球
				for(k=red; k<=black; k++) //第三个球的颜色
					if(k!=i&&k!=j)   //若三个球的颜色都不相同
					{
						n=n+1;  //排列总数加一
						for(int loop=1; loop<=3; loop++)
						{  //先后对三个球做处理
							switch(loop)
							{
								case 1: pri=color(i);break;
								case 2: pri=color(j);break;
								case 3: pri=color(k);break;
								default: break;
							}
							switch(pri)
							{// 输出颜色
								case red: cout<<setw(8)<<"red"; break;
								case yellow: cout<<setw(8)<<"yellow"; break;
								case blue: cout<<setw(8)<<"blue"; break;
								case white: cout<<setw(8)<<"white"; break;
								case black: cout<<setw(8)<<"black"; break;
								default: break;
							}
						}
						cout<<endl;
					}
	cout<<"total="<<n<<endl;
	return 0;
}

```
---
## 文件操作函数    
feof函数：可以检查文件读写位置标记是否移到文件的末尾，即磁盘文件是否读写结束，如是，函数返回值为1，否则为0.

----
预处理命令行不能以分号结尾，预处理命令行可以出现在程序的最后一行，**预处理命令行作用域是整个文件**。