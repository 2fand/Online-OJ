(每天更5题)
 
**BC1 Hello Nowcoder** 
```
#include <stdio.h>

int main() 
{    
    printf("Hello Nowcoder!");
    return 0;
}
```
 **BC2 小飞机** 
```
#include <stdio.h>

int main() {
    printf("     **     \n     **     \n************\n************\n    *  *    \n    *  *    ");
    return 0;
}
``` 
**BC3 牛牛学说话之-整数**
```
#include <stdio.h>

int main() {
    int i=0;
    scanf("%d",&i);
    printf("%d",i);
    return 0;
} 
```
**BC4 牛牛学说话之-浮点数**
```
#include <stdio.h>
int main() {
    float a=1.000000;
    int b,c=0;
    scanf("%f",&a);
    b=a*1000;
    c=a*10000;
    if (c-b*10>4) {b++;}
    printf("%.3f",b/1000.0000);
    return 0;
}
```
**BC5 牛牛学说话之-字符**
```
#include <stdio.h>

int main() {
    char i="1";
    scanf("%c",&i);
    printf("%c",i);
    return 0;
}
```
**BC6 牛牛的第二个整数**
```
#include <stdio.h>

int main() {
    int a=0;
    int b=0;
    int c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("%d",b);
    return 0;
}
```
**BC7 牛牛的字符矩形**
```
#include <stdio.h>

int main()
{
    char a=6;
    scanf("%c",&a);
    printf("%c%c%c\n%c%c%c\n%c%c%c",a,a,a,a,a,a,a,a,a);
    return 0;
}
```
**BC8 牛牛的字符菱形**
```
#include <stdio.h>

int main()
{
    char a=6;
    scanf("%c",&a);
    printf("  %c  \n %c%c%c \n%c%c%c%c%c\n %c%c%c \n  %c  ",a,a,a,a,a,a,a,a,a,a,a,a,a);
    return 0;
}
```
**BC9 字符转ASCII码**
```
#include <stdio.h>

int main()
{
    char a=6;
    scanf("%c",&a);
    printf("%d",a);
    return 0;
}
```


