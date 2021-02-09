# <font color=green>（1）考点9</font> 😁
# <font color=red>1.</font>
 ```
 #include <stdio.h>
 #define  S(x)  x*x
 #define  T(x)  S(x)*S(x)
 main()
 {  int  k=5, j=2;
    printf("%d,%d\n", S(k+j),T(k+j));
 }
 ```
 本题考查宏定义 以k+j直接代替x 则S(k+j)=k+j*k+j

# <font color=red>2.</font>
 ```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
struct stu {  
    char  *name, gender;
    int  score; 
};
main()
{  
    struct stu  a={NULL, 'm', 290}, b;
    a.name=(char *)malloc(10);
    strcpy(a.name, "Zhao");
    b = a;   b.gender = 'f';   b.score = 350; 
    strcpy(b.name, "Qian");
    printf( "%s,%c,%d,", a.name, a.gender, a.score );
    printf( "%s,%c,%d\n", b.name, b.gender, b.score );
}
```
本题考查指针。 b=a之后，b.name与a.name指向同一块内存区域，故调用strcpy(字符串复制函数)之后，b.name所指向的区域存储内容变为Qian,a.name所指向区域同。

# <font color=red>3.</font>
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
typedef struct stu {  
    char  *name, gender;
    int  score; 
} STU;
void f(char  *p)
{  
    p=(char *)malloc(10);   
    strcpy(p, "Qian");  
}
main()
{  
    STU  a={NULL, 'm', 290}, b;
    a.name=(char *)malloc(10);
    strcpy( a.name, "Zhao" );
    b = a;
    f(b.name);
    b.gender = 'f';   b.score = 350; 
    printf("%s,%c,%d,", a.name, a.gender, a.score);
    printf("%s,%c,%d\n", b.name, b.gender, b.score);
}

```
本题考查指针作为函数的形参，在调用f函数时，b.name作为f函数的实参传递给形参p，但进入f函数的函数体之后，只是对指针p进行操作，并且f函数调用结束后，形参p指针的值不会回传给实参b.name。故b.name与a.name所指向区域的内容未发生变化

# <font color=red>4.</font>
```
 typedef  int*  T;  
    T  a[10];
```
本题考查typedef 与 指针数组 T=int* 故 T a[10] = int * a[10]
*先与int结合，表示数据类型是int型指针，总体来看，表示一个维数为10的数组a 它的类型为int型指针   
# <font color=red>5.</font>
 ```
 #include <stdio.h>
 #include <string.h>
 typedef  struct stu {  char  name[10], gender;
                    int  score; 
                 } STU;
 void  f( char  *p )
 {  strcpy( p, "Qian" );  }
 main()
 {  STU  a={"Zhao", 'm', 290}, b;
    b=a;
    f(b.name);
    b.gender = 'f';    b.score = 350; 
    printf("%s,%c,%d,", a.name, a.gender, a.score);
    printf("%s,%c,%d\n", b.name, b.gender, b.score);
 }
```
本题考查 结构体成员地址作为函数实参。b.name是数组，b=a时，将a.name数组的内容赋给b.name数组，但b.name数组的首址不等于a.name的首址，故将b,name作为实参传入f函数并运行后，只会改变b.name的内容，不会改变a.name的内容

# <font color=red>6.</font>

```
typedef  int*  T;  
    T  a[10];

```
等价于 int* a[10]
```
typedef  char  T[10];  
    T  *a;
```
typedef  char  T[10];  
    T  *a;
# <font color=red>等价于char （*a）[10],这题参考牛客网.</font>
typedef  char  T[10];  的意思是 T的char[10]的新名 故 T *a相当于定义了一个指向char[10]的指针，
 
 
#include <stdio.h>
main()
{  
    char  c[2][5]={"6938","8254" }, *p[2];
    int  i, j, s=0;
    for( i=0; i<2; i++ )  p[i]=c[i]; 
    for( i=0; i<2; i++ )
        for( j=0; p[i][j]>0 ; j+=2 )  s=10*s+p[i][j]-'0';
    printf("%d\n",s); 
}

p[i][j]会取到'6'，会取到'3'，但是他们与整形进行运算时，按照ASCII表，分别表示54,51；
'0'表示48，结果'6'-'0'=6, '3'-'0'=3；实现了字符型数字到整型数字的转化。
以后我们想把字符型或字符串型数字，转化为表面上大小的整型数字的时候，也可以这么做。
~
在ASCII表中，'\0'表示的是0，在ASCII表的第一位。

# <font color=red>7.</font>
```
#include <stdio.h>
void main()
{
char c='0'; int b;
printf("%d\n",c);
b=c<<1;
printf("%d\n",b);

}
```
```
[Running] cd "e:\C-programming-review\" && gcc project1.c -o project1 && "e:\C-programming-review\"project1
48
96

[Done] exited with code=3 in 0.257 seconds

```

<font color=red>8.</font>
对指针p： p=0和p=NULL是等价的。

**位运算的对象只能是整型或字符型数据**

34.设有如下的说明和定义
    ```
    struct { 
        int a; 
        char *s; 
    } x, *p = &x; 
    x.a = 4; 
    x.s = "hello";
    ```
则以下叙述中正确的是    
答案：D   
A）语句 *p->s++; 等价于 (*p)->s++;

B）语句 ++p->a; 的效果是使p增1

C）(p++)->a与p++->a都是合语法的表达式，但二者不等价

D）语句 ++p->a; 的效果是使成员a增1

运算符优先级：（）大于 ->大于++ 大于*
故对A选项，P先与->结合，*p->s++等价于 *(p->s++)
++p->a等价于++(p->a)

```
# include <iostream>
using namespace std;
int main()
{
	 struct { 
        int a; 
        char *s; 
    } x, *p = &x, *q=&x;
    x.a = 4; 
    x.s = "hello";
cout<<p++->a<<endl;
cout<<p<<endl;
cout<<(q++)->a<<endl;
cout<<q<<endl;
return 0;
}
B选项中其实是等价的，看运行结果：
4
0019FF40
4
0019FF40
Press any key to continue
```
因为优先级 ()大于->大于++ 故加不加括号不影响结果，都是等价于
```
p->a
p++;
```

36.下面关于“EOF”的叙述，正确的是   
答案：A   
A）EOF是在库函数文件中定义的符号常量   
B）文本文件和二进制文件都可以用EOF作为文件结束标志   
C）对于文本文件，fgetc函数读入最后一个字符时，返回值是EOF   
D）EOF的值等于0   
解析：在C语言中，或更精确地说成C标准函数库中表示文件结束符（end of file）。在while循环中以EOF作为文件结束标志，这种以EOF作为文件结束标志的文件，**必须是文本文件。**在文本文件中，数据都是以字符的ASCII代码值的形式存放。我们知道，ASCII代码值的范围是0~255，不可能出现-1，因此可以用EOF作为文件结束标志,**EOF的值通常为-1**



# <font color=green>（2）考点7</font> 😁
# <font color=red>8.难</font>

```
代码段1：
 #include <stdio.h>
 int  k=7;
 void f(int  **s)
 {  int  *t=&k;
    *s=t;
    printf("%d,%d,%d,", k, *t, **s); 
 }
 main()
 {  int  i=3,*p=&i, **r = &p;
    f(r);     printf("%d,%d,%d\n", i, *p, **r); 
 }

运行结果：

[Running] cd "e:\C-programming-review\" && gcc project1.c -o project1 && "e:\C-programming-review\"project1
7,7,7,3,7,7
[Done] exited with code=6 in 0.524 seconds
```
分析：考点：**指针的指针**。   
本题各个变量的数据类型分别为：   
i,k为整型变量，   
p，t为整型指针，   
r,s为指针，不过它们所指向的内容还是指针。

<font color=red>难理解：</font>main函数中先让p指向i，即*p=i,再让r指向p,即 *r=p,**r= *p=i;再执行f（r），将r作为实参传给s，则 s=r, *s= *r=p，再让t指向k，即 *t=k,故此时 *s= *r=p=t,指针s所指向存储区域的内容变为t，又因为指针s和指针r指向同一片区域，故导致指针r所指向存储区域的内容变为t，又因为指针r所指向的区域为指针变量p的内容，故指针变量p的内容变为t，故在f函数调用结束后, **r= *p= *t=k=7.   
<font color=red>本题可与第3题对照着理解</font>，   
在第3题中，函数的参数是指针变量，而本题函数的参数是指针的指针，     
并且，在第3题中，并没有改变指针所指向的变量的值，改变的只是指针的值，故在函数调用完以后，函数外部作为实参的那个指针没有发生任何变化；而本题在所调用的函数中改变了指针所指向的变量的值，所以函数外部作为实参的指针和它所指向的变量的值都发生了变化。   
<font color=red>本题还可与以下代码段对照着理解</font>
```
代码段2： 
  #include <stdio.h>
 int  k=7,m=5;
 void  f(int  **s)
 {  int  *t=&k;
    s=&t;   *s=&m;   printf("%d,%d,%d,", k, *t, **s); 
 }
 main()
 {  int  i=3,*p=&i, **r = &p;  
    f(r);
    printf("%d,%d,%d\n",  i, *p, **r);
 }


 运行结果：

 7,5,5,3,3,3
Press any key to continue

```

&emsp;&emsp;上述代码段1和2的main函数部分都相同，但运行结果却不同，表现在**代码段1在执行完f函数之后，指针p和r所指向的内容发生了变化，而代码段2在执行完f函数之后，指针p和r所指向的内容未发生变化**。仔细分析会发现，
主要区别就在第8行和第27行。   
&emsp;&emsp;代码段1是`*s=t;`,而代码段2是`s=&t;`。看上去似乎没什么区别，但就是这两句的不同导致了运行结果的不同。 **`*s=t;`是改变指针s所指向变量的值，不改变指针s的值，即指针s原来指向哪里，现在还指向哪里**，又因为`s=r=p,`所以，`*s=*r=p=t=&k,`故在f函数执行结束后，`*p=**r=k=7。`     
&emsp;&emsp;而代码2是`s=&t;`**改变的是指针s的值，而不是指针所指向变量的值**，，所以执行完这条语句之后，s就不等于r了，即s和r不再指向同一个变量（p），所以后续对s的任何操作都不会引起r和p的变化。

<font color=red>9.</font>
```
 #include <stdio.h>
 void fun(int  a[ ], int  n)
 {  int  t,i,j;
    for (i=1; i<n; i+=2)
      for (j=i+2; j<n; j+=2)
        if (a[i] > a[j])  { t=a[i]; a[i]=a[j];a[j]=t;}
 }
 main()
 {  int  c[10]={10,9,8,7,6,5,4,3,2,1},i;
    fun(c, 10);
    for (i=0;i<10; i++)   printf("%d,", c[i]);
    printf("\n");
 }



[Running] cd "e:\C-programming-review\" && gcc project1.c -o project1 && "e:\C-programming-review\"project1
10,1,8,3,6,5,4,7,2,9,

[Done] exited with code=10 in 0.354 seconds
```
考点：数组名作为函数形参。    
分析：fun函数以数组名作为函数形参，编译系统在编译时，会将作为形参数组名当做指针处理，用来接收一个地址，在调用fun函数时，会将实参数组的首地址传递给形参数组名。因此，在fun函数中对数组元素值的更改，在fun函数调用结束后返回main函数时仍会保留。

-----
A）int* p1; int ** p2; int *p3;都是合法的定义指针变量的语句

B）语句p=NULL;执行后，指针p指向地址为0的存储单元

C）指针变量只能通过求地址运算符（&) 来获得地址值

D）语句p=NULL;与p=\0;是等价的语句
分析：B选项，P=NULL表示p不指向任何存储单元


36.以下叙述中正确的是   
答案：B    
A）语句 int a[4][3] = {{1,2}, {4,5}}; 是错误的初始化形式   
B）在逻辑上，可以把二维数组看成是一个具有行和列的表格或矩阵    
C）语句 int a[4][3] = {1,2,4,5}; 是错误的初始化形式   
D）语句 int a[][3] = {1,2,4,5}; 是错误的初始化形式
分析：考查二维数组的初始化，二维数组初始化时必须要指出第2维的大小，因为默认是按行初始化的。<font color=red>A选项是对的</font>

# <font color=green>（3）考点8</font> 😁
<font color=red>10.</font>
```
 #include <stdio.h>
 main()
 {  char  a[20], b[ ]="The sky is blue.";  int i;
    for (i=0; i<10; i++)  scanf("%c", &a[i]);
    a[i]='\0';
    gets(b);
    printf("%s%s\n", a,b);
 }

运行结果：
Fig flower is red.
Fig flower is red.
Press any key to continue
```
分析：gets函数是从stdin流中读取字符串到b中，在遇到回车符时会自动将其转换成'\0'加入到字符串的末尾。故在用for循环将Fig flower输入到a中以及调用gets函数之后，b中元素为_is red.'\0'is blue. 用printf输出为Fig flower is red.
scanf.
> gets函数的原型为 char *gets(* buffer),它会从stdin流中读取字符串，直到遇到换行符或EOF为止，并将读取到的字符存到buffer指针所指向的字符数组中，换行符不作为读取串的内容，而是被转换为'\0',作为字符串的结束标志，若读入成功，返回与参数buffer相同的字符指针，若读入过程中遇到EOF或发生错误，返回NULL指针。   

<font color=red>11.</font>

A）char  *s = "ABCDE" ;

B）char  *s ;  gets( s );

C）char  s[4][5] = { "ABCDE" };

D）char  s[5] = { 'A', 'B', 'C', 'D', 'E' };
选A  选项B是s是个野指针，不安全。选项D要想让S中存的是字符串，结尾应该是'\0'


<font color=red>12.</font>
```
 #include <stdio.h>
 void  fun( char  **p )
 {  int  i;
    for(i=0; i<4; i++ ) printf("%s",p[i]);
 }
 main()
 {  char  *s[6]={ "ABCD","EFGH","IJKL","MNOP","QRST","UVWX" } ;
    fun(s);    printf("\n"  );
 }
```

```
18.有以下程序
#include <stdio.h>
fun( int a, int b )
{  
    int  static  m=0, i=2;
    i=i+m+1;   
    m=i+a+b;
    return  m;
}
main()
{  
    int  k=4, m=1, p;
    p=fun( k, m); 
    printf("%d,",p);
    p=fun( k, m); 
    printf("%d\n",p);
}

分析：fun函数里面的m和main函数里面的m不是同一个m。
```

# <font color=green>（4）考点6</font> 😁
```
<font color=red>13.</font>
 #include <stdio.h>
    main()
    {  int  a=1,b=2,c=3,d=4;
       if ((a=2) || (b=1)) c=2;
       if ((c==3) && (d=-1)) a=5;
       printf("%d,%d,%d,%d\n", a,b,c,d);
    }
```
考点：在逻辑表达式的求解中，并不是所有的逻辑运算符都会被执行，只是在必须执行下一个逻辑运算符才能求出表达式的值时，才会执行该运算符

<font color=red>14.</font>
```
 #include <stdio.h>
    main()
    {  int  s=0, n;
       for (n=0; n<4; n++)  
       {  switch(n) 
         {  default:  s+=4;
            case 1:  s+=1;
            case 2:  s+=2;
            case 3:  s+=3;
         }
       }
       printf("%d\n", s); 
    }
 ```
分析：考查switch语句。在执行switch语句时，先计算switch后面表达式的值，然后再将其与各case标号比较，若都不相同，且有default标号，则执行default标号后面的语句。  可知，各case语句和default语句出现的先后结果并不影响执行结果（前提是每个标号后面的语句中最后一条都是break；）


<font color=red>15.</font>

```
A）'\x09'

B）'\x9d'

C）'\09'

D）'9'
```
考点：考查字符常量中的转移字符：'\ooo...ooo'其中o为八进制数
'\xhhhh...hhh'其中h为十六进制数。该转义字符即与该八进制数（十六进制数）对应的ASCII字符



 # 刷到了考点7第38题
 # 刷到了考点9第30题
 # 刷到了考点8第10题
 # 刷到了考点6第21题
