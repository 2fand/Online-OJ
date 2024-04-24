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
**BC10 实现四舍五入**
```
//目前还没做好
```
**BC11 成绩输入输出**
```
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("score1=%d,score2=%d,score3=%d",a,b,c);
    return 0;
}
}
```
**BC12 学生基本信息输入输出**
```
#include <stdio.h>

int main() {
    long long a=0;
    int d,e=0;
    float b,c,da=1.000;
    scanf("%lld;%f,%f,%f",&a,&b,&c,&da);
    d=b*100;
    e=b*1000;
    if (e-d*10>4) {d++;}
    b=d/100.000;
    d=c*100;
    e=c*1000;
    if (e-d*10>4) {d++;}
    c=d/100.000;
    d=da*100;
    e=da*1000;
    if (e-d*10>4) {d++;}
    da=d/100.000;
    printf("The each subject score of No. %d is %.2f, %.2f, %.2f.",a,b,c,da);
    return 0;
}
```
**BC13 出生日期输入输出**
```
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%4d%2d%2d",&a,&b,&c);
    printf("year=%d\nmonth=%02d\ndate=%02d",a,b,c);
    return 0;
}
```
**BC14 按照格式输入并交换输出**
```
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("a=%d,b=%d",&a,&b);
    printf("a=%d,b=%d",b,a);
    return 0;
}
```
**BC15 大小写转换**
```
//目前还没做好
```
**BC16 十六进制转十进制**
```
#include <stdio.h>

int main() {
    printf("%15d",11259375);
    return 0;
}
```
**BC17 缩短二进制**
```
#include <stdio.h>

int main() {
    printf("%#o %#X",1234,1234);
    return 0;
}
```
**BC18 牛牛的空格分隔**
```
#include <stdio.h>

int main() {
    char a=0;
    int b=0;
    float c=0.01;
    scanf("%c %d %f",&a,&b,&c);
    printf("%c %d %f",a,b,c);
    return 0;
}
```
**BC19 牛牛的对齐**
```
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("%d       %d       %d",a,b,c);
    return 0;
}
```
**BC20 进制A+B**
```
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%x %o",&a,&b);
    printf("%d",a+b);
    return 0;
}
```
**BC21 牛牛学加法**
```
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",a+b);
    return 0;
}
```
**BC22 牛牛学除法**
```
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",a/b);
    return 0;
}
```
**BC23 牛牛学取余**
```
#include <stdio.h>

int main()
{
    int a, b, c, d = 0;
    scanf("%d %d",&a,&b);
    c = b;
    for (b = b; b < a; b = b + c) { d = b; }
    printf("%d", a - d);
    return 0;
 
}
```
**BC25 牛牛买电影票**
```
#include <stdio.h>

int main() {
    int x=0;
    scanf("%d",&x);
    printf("%d",x*100);
    return 0;
}
```
**BC26 计算带余除法**
```
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d",&a,&b);
    c=a/b;
    printf("%d %d",c,a-b*c);
    return 0;
}
```
**BC27 整数的个位**
```
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d",&a);
    b=a/10;
    printf("%d",a-b*10);
    return 0;
}
```
**BC28 整数的十位**
```
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d",&a);
    b=a/10;
    c=a/100;
    printf("%d",b-c*10);
    return 0;
}
```
**BC29 开学？**
```
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d",&a,&b);
    a=a+b;    
    c=a/7;
    b=a-c*7;
    if (b==0) {b=7;}
    printf("%d",b);
    return 0;
}
```
**BC30 时间转换**
```
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d",&a);
    b=a/3600;
    a=a-b*3600;
    c=a/60;
}
```
**BC31 2的n次方计算**
```
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%d",2<<(a-1));
    return 0;
}
```
**BC32 你能活多少秒**
```
#include <stdio.h>

int main() {
    int age=0;
    scanf("%d",&age);
    printf("%lld0000",age*3156);
    return 0;
}
```
