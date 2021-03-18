```
#include <stdio.h>
#include <string.h>

   int main()
	{
	   typedef char * T[10];
	   T a;
	   char *b[10];
	   char (*c)[10];
	   printf("&a=%d\n",a);
	   printf("&(a+1)=%d\n",a+1);
	   printf("&b=%d\n",b);
	   printf("&(b+1)=%d\n", b+1);
	   printf("&c=%d\n",c);
	   printf("&(c+1)=%d\n",c+1);
		int d[2];
		printf("&d=%d\n",d);
		printf("&(d+1)=%d\n",(d+1));

		return 0;
    }


```