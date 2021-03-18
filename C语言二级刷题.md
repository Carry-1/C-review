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

# <font color=red>42.</font>
```
若fp已定义为指向某文件的指针，且没有读到该文件的末尾，则C语言函数feof(fp)的函数返回值是
答案：B
A）EOF
B）0
C）-1
D）非0
```
考察feof函数，即end of file 如果fp已指向文件末尾，则返回1，否则返回0

```
45.以下叙述中错误的是
答案：CA）typedef的作用是用一个新的标识符来代表已存在的类型名
B）用typedef可以说明一种新的类型名
C）typedef说明的新类型名必须使用大写字母，否则会出编译错误
D）可以用typedef说明的新类型名来定义变量
```
分析：选项C肯定是错的，例如在定义单链表的结点时，有小写。
选项B,typedef不是给已经存在的类型取一个别名么？

```
47.若有定义语句
    int  b = 2;
则表达式 ( b<<2 ) / ( 3 || b )的值是
答案：C
A）4
B）2
C）8
D）0
```
分析：注意|与||的区别，前者是按位或，后者是逻辑或，后者运算结果只可能为0或者1

```
48.有以下程序
 #include <stdio.h>
 main()
 {  FILE  *fp;     int  i, a[6] = {1,2,3,4,5,6};
    fp = fopen( "d2.dat", "w+" );
    for (i=0; i<6; i++)    fprintf( fp, "%d\n", a[i] );
    rewind( fp );
    for ( i=0; i<6; i++ )   fscanf( fp, "%d", &a[5-i] );
    fclose(fp);
    for ( i=0; i<6; i++ )   printf( "%d,", a[i] );
 }
程序运行后输出结果是
答案：AA）6,5,4,3,2,1,

B）1,2,3,4,5,6,

C）4,5,6,1,2,3,

D）1,2,3,3,2,1,

分析： fprintf函数输入到文件中，fscanf函数是从文件中输入
```
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


<font color=green>考点5</font>
```
3.关于C语言的符号常量，以下叙述中正确的是
答案：D
A）符号常量的符号名是标识符，但必须大写

B）符号常量在整个程序中其值都不能再被重新定义

C）符号常量的符号名必须是常量

D）符号常量是指在程序中通过宏定义用一个符号名来代表一个常量

A、B选项见如下代码
# include<stdio.h>
# define N 5
# define N 6
# define n 7
int main()
{
	printf("%d\n",N);
	printf("%d\n",n);

	return 0;
}

6
7
Press any key to continue


```
C选项符号常量的符号名是标识符，而不应是1，2，3等常量


```
4.若有以下程序
    #include <stdio.h>
    main()
    {  int  b=10, a=-11;
       a %= b %= 4;
       printf("%d %d\n", a, b);
    }
则程序的输出结果是
答案：B
A）-1  -2

B）-1  2

C）1  2

D）1  -2
```
```
4.若有以下程序
    #include <stdio.h>
    main()
    {  int  b=10, a=-11;
       a %= b %= 4;
       printf("%d %d\n", a, b);
    }
则程序的输出结果是
答案：B
A）-1  -2

B）-1  2

C）1  2

D）1  -2
```
**分析：VC++6.0编译系统对/和%运算结果向零取整，即取更靠近0的结果。因此，对于-11%2.乍一看可能有两种结果： 1.-11%2=1（商为-6）2.-11%2=-1(商为-5)应使余数与被除数同号，故-11%2=-1。**

```
5.若有以下程序
    #include <stdio.h>
    main()
    {  int  a=0,b=0,c=0; 
       c= (a -= ++a), (a+=b, b+=4);
       printf("%d,%d,%d\n",a,b,c);
    }
则程序的输出结果是
答案：B
A）0,4,4

B）0,4,0

C）1,4,4

D）1,4,1


```
分析：本题重要的是看懂a -= ++a，实际上，因为赋值运算符的结合方向是自右向左，因此，先执行a+1 ,再执行 a= a-a=0;   
等价于：
```
# include<stdio.h>
int main()
{
	int a =4;
	//a-=++a;   结果为0
	a=a-(++a);   //结果也为0
	printf("%d\n",a);
return 0;
}

运行结果：
0
Press any key to continue
```

### 1.预定义标识符是系统预先定义的标识符，用户可以重复定义，但是会覆盖掉系统已定义过的标识符。      
### 2.printf中`“”`引起来的是格式控制字符串，%d表示以十进制数形式输出带符号整数，%o表示以八进制数形式输出无符号整数，%x表示以十六进制数形式输出无符号整数。    
### 3.C语言中强制类型转换需要将类型说明符给括起来，因此不能写成int(a+b),而应写成(int)a+b的形式。    
### 4.C语言中表达式的类型取决于表达式的值的类型，若表达式的值是一个整数，则为整型表达式
### 5.printf中"%"主要用于指定输出形式，若为"%%"则表示输出一个普通字符"%"
### 6.八进制整数常以0作为前缀，十六进制整数常以0x作为前缀
### 7.在C语言中，NULL等价于0，故
```
int *p;
p = NULL; //等价于 p = 0;
```
因为NULL的ASCII码为0， 而'0'的ASCII码为48， 故显然`p=NULL不等于p='0'`
### 8. C语言中常量存放在内存的常量区，不可寻址。
```
int a=3;
int *p;
p = &a;
int **q;
q = &p;
```
指针p是整型指针变量，意思是它指向一个整型变量，而指针q是一个指针类型的指针变量，意思是它指向一个指针变量，取指针变量p的地址不能赋值给它自身，因为指针p是指向整型变量的指针，而不是指向指针变量的指针。故取p的地址只能赋值给q

### 9.科学计数法中，e/E后面必须有数字并且后面的数字为整数
### 10.数值型常量包括整型常量，实型常量和字符型常量，字符型常量用单引号括起来，而不是双引号。
### 11.赋值语句的左边必须是变量，不能是表达式。
例如:`a+b=c;`这个表达式就是错误的，因为编译器会表达式从左往右扫描，首先扫描到a+b，这是个表达式，计算出结果，再扫描到'='进行赋值运算，出错，因为左边不是一个变量。
### 12.scanf是库函数名，属于预定义标识符，可以被用户重新定义，case是关键字，不可被用户重新定义。
### 13.存放地址值的变量称为指针变量，由于所有地址值所占的字节数都一样，故任意类型的指针变量所占的内存大小都一样。由于一个变量的地址（指向某个变量的指针）还隐含有类型信息，因此不可以将指针随便乱指，只能指向与指针类型相同的变量。
### 14.变量的存储类别
### 15.用字符数组在存储字符串时，会自动在字符数组后面加上一个字符串结束标志。在32位编译器上，字符指针（地址）占4个字节，而在64位编译器上，字符指针占8B，故
```
#include <stdio.h>
    int main()
	{
		int a =3; 
	char *str1 = "Hello";
	char str2[] = "Hello";
	printf("%d%d%d\n", sizeof(&a),sizeof(str1), sizeof(str2));
 			return 0;
    }
```
在GCC编译器（64位）上编译运行，输出为886。sizeof(str1)为求字符串的字符个数，包括结尾符。而strlen(str1)为求字符串的实际字符个数，不包括结尾符。
    
 字符串中的字符依次存储在内存中一块连续的区域内，并且把空字符' \0'自动附加到字符串的尾部作为字符串的结束标志。故字符个数为n的字符串在内存中应占（n+1）个字节。语句char str[10] ="string!"; 和char str[10]={"string!"}; 等价，可以使用字符串常量来给一维字符数组赋值，在语句char str[]="string!";中数组str长度比字符串长度小一个字节，字符串中包含隐含的结尾符。

<font color=red> 关于字符串的初始化：</font>
`char str1[]="str1";`则字符数组将包含5个元素。（易忘）即用字符串对未指明长度的字符数组初始化时，编译器会自动在末尾加上一个结束符'\0'。而字符数组的最后一个元素不一定必须为'\0',这是显然的，因为字符数组不一定是用来存放字符串的，它可能只是用来存放一个个不相关的字符。而如果这样来定义字符串`char str[] = {'s','t','r','1','\0'};`则结尾的'\0'是必须的。

<font color=red>字符串数组，是指数组中的每个元素都是一个存放字符串的一维数组，意思是每个元素都是一个数组，且这个字符串数组实际上是二维数组。</font>

<font color=red>两个字符串不可以用关系运算符比较大小么</font>
```
#include <stdio.h>
#include <string.h>
    int main()
	{
		printf("%d\n",strlen("a"));
	
return 0;
    }

1
Press any key to continue
```
由运行结果可知strlen函数返回的是字符串占用内存空间的实际长度，不包括结尾符。

<font color=red>printf函数在输出时的一些格式问题</font>
```
#include <stdio.h>

    int main()
	{
		int a = 1234;
		double d = 123.1415;
		printf("%1.3lf\n",d);
		return 0;
    }
123.141
Press any key to continue
```
```
#include <stdio.h>

    int main()
	{
		int a = 1234;
		double d = 123.1415;
		printf("%3d %1.3lf\n",a,d);
		return 0;
    }

1234 123.141
Press any key to continue
```

```
#include <stdio.h>

    int main()
	{
		int a = 1234;
		double d = 123.1415;
		printf("%5d\n",a);
		printf("%9.3lf\n",d);

		return 0;
    }
 1234
  123.141
Press any key to continue

```
```
#include <stdio.h>
#include <string.h>

    int main()
	{
		int a = 1234;
		double d = 123.1415678;
		printf("%5d\n",a);
		printf("%9.3lf\n",d);

		return 0;
    }

 1234
  123.141
Press any key to continue
```
`printf("%m.nf",d);`可见，对于形如%m.nf的浮点数，若其整数位数>m 则输出整数部分的全部位数，若其整数位数小于m且m小于总位数,则整数部分+小数部分（包括小数点）总共输出m位，小数部分四舍五入，整数部分左边留空格。 若m大于全部位数，则全部输出。左边留空格

```
#include <stdio.h>
#include <string.h>

    int main()
	{
		typedef char T[10];
		T *a;
		char (*b)[10];
		char *c;
		char *d[10];
		printf("&a=%d\n", a);
		printf("&(a+1)=%d\n", a+1);
		printf("&b=%d\n", b);
		printf("&(b+1)%d\n", b+1);
		printf("&c=%d\n", c);
		printf("&(c+1)=%d\n", c+1);
		printf("&d=%d\n", d);
		printf("&(d+1)=%d\n", d+1);
		return 0;
    }

    运行结果：
&a=-858993460
&(a+1)=-858993450
&b=-858993460
&(b+1)-858993450
&c=-858993460
&(c+1)=-858993459
&d=1703692
&(d+1)=1703696
Press any key to continue


```
`~i;`表示对i按位取反
