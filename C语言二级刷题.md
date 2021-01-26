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
**位运算的对象只能是整型或字符型数据**
# <font color=green>（2）考点7</font> 😁
# <font color=red>8.难</font>

```
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
```
运行结果：
```
[Running] cd "e:\C-programming-review\" && gcc project1.c -o project1 && "e:\C-programming-review\"project1
7,7,7,3,7,7
[Done] exited with code=6 in 0.524 seconds
```
分析：考点：指针的指针。   
本题各个变量的数据类型分别为：   
i,k为整型变量，   
p，t为整型指针，   
r,s为指针，不过它们所指向的内容还是指针。

<font color=red>难理解：</font>main函数中先让p指向i，即*p=i,再让r指向p,即 *r=p,**r= *p=i;再执行f（r），将r作为实参传给s，则 s=r, *s= *r=p，再让t指向k，即 *t=k,故此时 *s= *r=p=t,指针s所指向存储区域的内容变为t，又因为指针s和指针r指向同一片区域，故导致指针r所指向存储区域的内容变为t，又因为指针r所指向的区域为指针变量p的内容，故指针变量p的内容变为t，故在f函数调用结束后, **r= *p= *t=k=7.   
<font color=red>本题可与上面的第3题对照着理解</font>，   
在第3题中，函数的参数是指针变量，而本题函数的参数是指针的指针，     
并且，在第3题中，并没有改变指针所指向的变量的值，改变的只是指针的值，故在函数调用完以后，函数外部作为实参的那个指针没有发生任何变化；而本题在所调用的函数中改变了指针所指向的变量的值，所以函数外部作为实参的指针和它所指向的变量的值都发生了变化。







 # 刷到了考点7第5题
 # 刷到了考点9第30题
 #