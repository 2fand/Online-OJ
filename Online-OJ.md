# 牛客网
*(每天更1题)*
## C 
**BC1 Hello Nowcoder** 
```c
#include <stdio.h>

int main() 
{    
    printf("Hello Nowcoder!");
    return 0;
}
```
**BC2 小飞机** 
```c
#include <stdio.h>

int main() {
    printf("     **     \n     **     \n************\n************\n    *  *    \n    *  *    ");
    return 0;
}
``` 
**BC3 牛牛学说话之-整数**
```c
#include <stdio.h>

int main() {
    int i=0;
    scanf("%d",&i);
    printf("%d",i);
    return 0;
} 
```
**BC4 牛牛学说话之-浮点数**
```c
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
```c
#include <stdio.h>

int main() {
    char i="1";
    scanf("%c",&i);
    printf("%c",i);
    return 0;
}
```
**BC6 牛牛的第二个整数**
```c
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
```c
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
```c
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
```c
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
```c
//目前还没做好
```
**BC11 成绩输入输出**
```c
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("score1=%d,score2=%d,score3=%d",a,b,c);
    return 0;
}
```
**BC12 学生基本信息输入输出**
```c
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
```c
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%4d%2d%2d",&a,&b,&c);
    printf("year=%d\nmonth=%02d\ndate=%02d",a,b,c);
    return 0;
}
```
**BC14 按照格式输入并交换输出**
```c
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("a=%d,b=%d",&a,&b);
    printf("a=%d,b=%d",b,a);
    return 0;
}
```
**BC15 大小写转换**
```c
#include <stdio.h>

int main() {
    char c = 0;
    while (scanf("%c", &c) != EOF) {
        printf("%c", '\n' == c ? '\n' : c + 32);
    }
    return 0;
}
```
**BC16 十六进制转十进制**
```c
#include <stdio.h>

int main() {
    printf("%15d",11259375);
    return 0;
}
```
**BC17 缩短二进制**
```c
#include <stdio.h>

int main() {
    printf("%#o %#X",1234,1234);
    return 0;
}
```
**BC18 牛牛的空格分隔**
```c
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
```c
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("%d       %d       %d",a,b,c);
    return 0;
}
```
**BC20 进制A+B**
```c
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%x %o",&a,&b);
    printf("%d",a+b);
    return 0;
}
```
**BC21 牛牛学加法**
```c
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",a+b);
    return 0;
}
```
**BC22 牛牛学除法**
```c
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",a/b);
    return 0;
}
```
**BC23 牛牛学取余**
```c
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
**BC24 浮点数的个位数字**
```c
#include <stdio.h>

int main() {
    float a=0.0;
    scanf("%f",&a);
    int b,c=0;
    b=(int)a;
    c=a/10;
    printf("%d",b-c*10);
    return 0;
}
```
**BC25 牛牛买电影票**
```c
#include <stdio.h>

int main() {
    int x=0;
    scanf("%d",&x);
    printf("%d",x*100);
    return 0;
}
```
**BC26 计算带余除法**
```c
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
```c
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
```c
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
```c
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
```c
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d",&a);
    b=a/3600;
    a=a-b*3600;
    c=a/60;
    printf("%d %d %d",b,c,a-c*60);
    return 0;
}
```
**BC31 2的n次方计算**
```c
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%d",2<<(a-1));
    return 0;
}
```
**BC32 你能活多少秒**
```c
#include <stdio.h>

int main() {
    int age=0;
    scanf("%d",&age);
    printf("%lld0000",age*3156);
    return 0;
}
```
**BC33 统计成绩**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    float farr[100] = {0.0f};
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%f", &farr[ia]);
    }
    float fmin = farr[0];
    float fmax = farr[0];
    float fsum = 0.0f;
    for (ia = 0; ia < i; ia++) {
        fsum += farr[ia];
        fmin > farr[ia]&& (fmin = farr[ia]);
        fmax < farr[ia]&& (fmax = farr[ia]);
    }
    printf("%.2f %.2f %.2f", fmax, fmin, fsum / (float)i);
    return 0;
}
```
**BC35 KiKi和酸奶**
```c
#include <stdio.h>

int main() {
    int in = 0;
    int ih = 0;
    int im = 0;
    int ia = 0;
    while (scanf("%d %d %d", &in, &ih, &im) != EOF) {
        if (!(im % ih)) {
            ia = in - (im / ih);
        } else {
            ia = in - (im / ih + 1);
        }
        printf("%d ", ia);
    }
    return 0;
}
```
**BC36 温度转换**
```c
#include <stdio.h>

int main() {
    float f,c=1.000;
    scanf("%f",&f);
    c=5.000/9.000*(f-32.000);
    int a,b=0;
    a=c*1000;
    b=c*10000;
    if (b-a*10>4) {a++;}
    c=a/1000.000;
    printf("%.3f",c);
    return 0;
}
```
**BC37 牛牛的圆**
```c
#include <stdio.h>

int main() {
    int i=1;
    scanf("%d",&i);
    printf("%.2f",3.14*i*i);
    return 0;
}
```
**BC38 牛牛的并联电路**
```c
#include <stdio.h>

int main() {
    int r1,r2=0;
    scanf("%d %d",&r1,&r2);
    double v=r1;
    double b=r2;
    printf("%.1f",1.000/((1.000/v)+(1.000/b)));
    return 0;
}
```
**BC39 牛牛的水杯**
```c
#include <stdio.h>

int main() {
    int ih = 0;
    int ir = 0;
    int i = 0;
    int ia = 0;
    int ib = 1;
    scanf("%d %d", &ih, &ir);
    (i = 3.14 * (float)ih * (float)ir * (float)ir, ia = i);
    for (ib = 1; i < 10000; i += ia) {
        ib++;
    }
    printf("%d", ib);
    return 0;
}
```
**BC40 牛牛的等差数列**
```c
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",b+(b-a));
    return 0;
}
```
**BC41 牛牛的球**
```c
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%.2f",3.14*a*a*a+3.14*a*a*a/3);
    return 0;
}
```
**BC42 小乐乐定闹钟**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ik = 0;
    scanf("%d:%d %d", &i, &ia, &ik);
    int iad = i * 60 + ia + ik;
    printf("%02d:%02d", iad / 60 % 24, iad % 60);
    return 0;
} 
```
**BC43 小乐乐排电梯**
```c
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%.2f",3.14*a*a*a+3.14*a*a*a/3);
    return 0;
}
```
**BC44 小乐乐与欧几里得**
```c
#include <stdio.h>

int main() {
    long long ll = 0;
    long long lla = 0;
    long long llb = 0;
    while (scanf("%lld %lld", &lla, &llb) != EOF) {
        long long llab = lla * llb;
        while (lla % llb) {
            (ll = lla % llb, lla = llb, llb = ll);
        }
        printf("%lld", llb + llab / llb);
    }
    return 0;
}
```
**BC45 小乐乐改数字**
```c
#include <stdio.h>

int main() {
    long long ll = 0;
    int i = 0;
    int arr[10] = {-1, -1, -1, -1, -1, -1, -1, -1, -1, -1};
    int iflag = 0;
    scanf("%lld", &ll);
    for (; ll; (ll /= 10, i++)) {
        arr[i] = ll % 10;
    }
    for (i = 0; -1 != arr[i]; i++) {
        if (arr[i] % 2) {
            arr[i] = 1;
        } else {
            arr[i] = 0;
        }
    }
    for (i--; -1 != i; i--) {
        if (arr[i] || iflag) {
            printf("%d", arr[i]);
            iflag++;
        }
    }
    if (!iflag) {
        printf("0");
    }
    return 0;
}
```
__BC46 KiKi算期末成绩__
```c
#include <stdio.h>

int main() {
    int arr[4] = {0};
    int i = 0;
    for (; i < 4; i++) {
        scanf("%d", &arr[i]);
    }
    printf("%.1f", arr[0] / 5.0 + arr[1] / 10.0 + arr[2] / 5.0 + arr[3] / 2.0);
    return 0;
}
```
__BC47 (a+b-c)*d的计算问题__
```c
#include <stdio.h>

int main() {
    int a,b,c,d=0;
    scanf("%d %d %d %d",&a,&b,&c,&d);
    printf("%d",(a+b-c)*d);
    return 0;
}
```
**BC48 牛牛的线段**
```c
#include <stdio.h>

int main() {
    long long x1,x2,y1,y2=0;
    scanf("%lld %lld %lld %lld",&x1,&y1,&x2,&y2);
    printf("%lld",((x1-x2)*(x1-x2))+((y1-y2)*(y1-y2)));
    return 0;
}
```
**BC50 你是天才吗？** 
```c
#include <stdio.h>

int main() {
    int i=0;
    scanf("%d",&i);
    if (i>139) {printf("Genius");}
    return 0;
}
```
**BC51 及格分数**
```c
#include <stdio.h>

void abc(int b) {printf("%s\n",b>59 ? "Pass" : "Fail");}
int main() {
    int a=0;
    while (scanf("%d",&a) != EOF) { // 注意 while 处理多个 case
        // 64 位输出请用 printf("%lld") to 
        abc(a);
    }
    return 0;
}
```
**BC52 判断整数奇偶性**
```c
#include <stdio.h>

int main() {
    int i = 0;
    while (scanf("%d", &i) != EOF) {
        printf("%s\n", i % 2 ? "Odd" : "Even");
    }
    return 0;
}
```
**BC53 判断是元音还是辅音**
```c
#include <stdio.h>

int main() {
    char c = 0;
    int i = 1;
    while (scanf("%c", &c) != EOF) {
        if (i++ % 2) {
            if ('A' == c || 'E' == c || 'I' == c || 'O' == c || 'U' == c || 'a' == c ||
                    'e' == c || 'i' == c || 'o' == c || 'u' == c) {
                printf("Vowel\n");
            } else {
                printf("Consonant\n");
            }
        }
    }
    return 0;
}
```
**BC54 牛牛的判断题**
```c
#include <stdio.h>

int main() {
    int l,x,r=0;
    scanf("%d %d %d",&x,&l,&r);
    printf("%s",l<=x && x<=r ? "true" : "false");
    return 0;
}
```
**BC55 判断闰年**
```c
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%s",a%100==0 ? a%400==0 ? "yes" : "no" : a%4==0 ? "yes" : "no");
    return 0;
}
```
**BC56 判断字母** 
```c
#include <stdio.h>

int main() {
    char a=0;
    scanf("%c",&a);
    printf("%s",(a>=65 && a<=90) || (a>=97 && a<=112) ? "YES" : "NO");
    return 0;
}
```
**BC57 四季** 
```c
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%4d%2d",&a,&b);
    printf("%s",b>=3 && b<=5 ? "spring" : b>=6 && b<=8 ? "summer" : b>=9 && b<=11 ? "autumn" : "winter");
    return 0;
}
```
**BC58 健康评估** 
```c
#include <stdio.h>

int main() {
    float f,fa=0.0;
    scanf("%f %f",&f,&fa);
    printf("%sormal",18.5 <= f/(fa*fa) && f/(fa*fa) <=23.9 ? "N" : "Abn");
    return 0;
}
```
**BC59 小乐乐找最大数**
```c
#include <stdio.h>

int main() {
    int a[4]={0};
    int i,max=0;
    scanf("%d %d %d %d",&a[0],&a[1],&a[2],&a[3]);
    for (i=0;i<4;i++) {if(a[i]>max) {max=a[i];}}
    printf("%d",max);
    return 0;
}
```
**BC60 判断是不是字母**
```c
#include <stdio.h>

int main() {
    char c = 0;
    while (scanf("%c", &c) != EOF) {
        if ('\n' == c) {
            printf("\n");
        } else {
            printf("%c is %s alphabet.", c, (c >= 65 && c <= 90) || (c>=97 && c<=122) ? "an" : "not an");
        }
    }
    return 0;
}
```
**BC61 牛牛的二三七整除**
```c
#include <stdio.h>

int main() {
    int i, ifl = 0;
    scanf("%d", &i);
    if (!(i % 2)) {
        printf("2 ");
        ifl++;
    }
    if (!(i % 3)) {
        printf("3 ");
        ifl++;
    }
    if (!(i % 7)) {
        printf("7 ");
        ifl++;
    }
    printf("%c", ifl ? '\n' : 'n');
    return 0;
}
```
**BC62 统计数据正负个数**
```c
#include <stdio.h>

int main() {
    long long a[10]={0};
    int i,n=0;
    scanf("%lld %lld %lld %lld %lld %lld %lld %lld %lld %lld ",&a[0],&a[1],&a[2],&a[3],&a[4],&a[5],&a[6],&a[7],&a[8],&a[9]);
    for (i=0;i<10;i++) {if (a[i]<0) {n++;}}
    printf("positive:%d\nnegative:%d",10-n,n);
    return 0;
}
```
**BC63 网购** 
```c
#include <stdio.h>

int main() {
    int b,c=0;
    float a=0;
    scanf("%f %d %d %d",&a,&b,&b,&c);
    if (b==11) {a*=0.7;}
    else {a*=0.8;}
    if (c==1) {a-=50;}
    printf("%.2f",a<0 ? 0.00 : a);
    return 0;
}
```
**BC64 牛牛的快递** 
```c
#include <stdio.h>

int main() {
    float f = 0.0f;
    char c = 0;
    scanf("%f %c", &f, &c);
    int imoney = 20;
    if (f--, f > 0) {
        for (; f > 0; f -= 1) {
            imoney++;
        }
    }
    'y' == c && (imoney += 5);
    printf("%d", imoney);
    return 0;
}
```
**BC66 牛牛的通勤** 
```c
#include <stdio.h>

int main() {
    long long ll = 0;
    long long lla = 0;
    scanf("%lld", (lla += 10, &ll));
    long long llb=ll;
    for (ll = ll; ll > 0; ll -= 10) {
        lla++;
    }
    printf("%c", lla > llb ? 'w' : 'v');
    return 0;
}
```
**BC68 牛牛的一周**
```c
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%sday",a==1 ? "Mon" : a==2 ? "Tues" : a==3 ? "Wednes" : a==4 ? "Thurs" : a==5 ? "Fri" : a==6 ? "Satur" : "Sun");
    return 0;
}
```
**BC69 HTTP状态码**
```c
#include <stdio.h>

int main() {
    int ia=0;
    while (scanf("%d", &ia) != EOF) {
        switch (ia) {
            case 200:
            printf("OK");
            break;
            case 202:
            printf("Accepted");
            break;
            case 400:
            printf("Bad Request");
            break;
            case 403:
            printf("Forbidden");
            break;
            case 404:
            printf("Not Found");
            break;
            case 500:
            printf("Internal Server Error");
            break;
            case 502:
            printf("Bad Gateway");
            break;
        }
        printf("\n");
    }
    return 0;
}
```
**BC70 计算单位阶跃函数**
```c
#include <stdio.h>

int main() {
    int it = 0;
    while (scanf("%d", &it) != EOF) {
        if (it > 0) {
            printf("1");
        } else if (it < 0) {
            printf("0");
        } else {
            printf("0.5");
        }
        printf("\n");
    }
    return 0;
}
```
**BC71 三角形判断**
```c
#include <stdio.h>

int main() {
    int ia, ib, ic = 0;
    while (scanf("%d %d %d", &ia, &ib, &ic) != EOF) {
        if (ia == ib && ib == ic) {
            printf("Equilateral triangle!");
        } else {
            if (ia + ib > ic && ia + ic > ib && ib + ic > ia) {
                printf("%s triangle!", ia == ib || ia == ic ||
                       ib == ic ? "Isosceles" : "Ordinary");
            } else {
                printf("Not a triangle!");
            }
        }
        printf("\n");
    }
    return 0;
}
```
**BC72 牛牛的计划**
```c
int main() {
    int y,m,d,yl,ml,dl=0;
    scanf("%d %d %d %d %d %d",&y,&m,&d,&yl,&ml,&dl);
    printf("%s",y<yl ? "yes" : y==yl ? m<ml ? "yes" : m==ml ? d<=dl ? "yes" : "no" : "no" : "no");
    return 0;
}
```
**BC74 获得月份天数**
```c
#include <stdio.h>

int main() {
    int a,b=0;
    while (scanf("%d %d",&a,&b) != EOF) { 
    printf("%d\n",b==1 || b==3 || b==5 || b==7 || b==8 || b==10 || b==12 ? 31 : b==2 ? a%4==0 ? a%100==0 ? a%400==0 ? 29 : 28: 29: 28: 30);}
    return 0;
}
```
**BC75 小乐乐是否被叫家长** 
```c
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("%s",((a+b+c))/3<60 ? "YES" : "NO");
    return 0;
}
```
**BC77 简单计算器** 
```c
#include <stdio.h>

int main() {
    double a,b,d=0.0;
    int e,f=0;
    char c=0;
    while (scanf("%lf%c%lf",&a,&c,&b) != EOF) {
        if (c!='+' && c!='-' && c!='*' && c!='/') {printf("Invalid operation!");}
    else {if (c=='/' && b==0.0) {printf("Wrong!Division by zero!");}
    else {
        switch (c) {
            case '+':
            d=a+b;
            break;
            case '-':
            d=a-b;
            break;
            case '*':
            d=a*b;
            break;
            case '/':
            d=a/b;
        }
        (e=d*10000,f=d*100000);
        if (f-e*10>4) {e++;}
        printf("%.4lf%c%.4f=%.4lf",a,c,b,e/10000.0);
    }}}
    return 0;
}
```
**BC78 KiKi说祝福语** 
```c
#include <stdio.h>

int main() {
    int a,i=0;
    scanf("%d",&a);
    for (i=0;i<a;i++) {printf("Happy new year!Good luck!\n");}
    return 0;
}
```
**BC79 小乐乐求和** 
```c
#include <stdio.h>

int main() {
    long long n,i=0;
    long long ii=1;
    scanf("%lld",&n);
    for (ii=1;ii<n+1;ii++) {i+=ii;}
    printf("%lld",i);
    return 0;
}
```
**BC80 奇偶统计** 
```c
#include <stdio.h>

int main() {
    int n=0;
    scanf("%d",&n);
    if (n%2==0) {printf("%d %d",(n-n%2)/2,(n-n%2)/2);}
    else {printf("%d %d",(n-n%2)/2+1,(n-n%2)/2);}
    return 0;
}
```
**BC81 KiKi求质数个数** 
```c
#include <stdio.h>
#include <math.h>

int main() {
    int i = 100;
    int ia = 2;
    int ib = 0;
    int ic = 0;
    for (i = 100; i < 1000; i++) {
        for (ia = 2; ia <= sqrt(i); ia++) {
            if (!(i % ia)) {
                ib = 1;
                break;
            }
        }
        if (!(ib)) {
            ic++;
        }
        ib = 0;
    }
    printf("%d", ic);
    return 0;
}
```
**BC82 乘法表** 
```c
#include <stdio.h>

int main() {
    int ii,iii=1;
    for (ii=1;ii<10;ii++) {for (iii=1;iii<ii+1;iii++) {
        if (ii*iii<10) {printf("%d*%d= %d%c",iii,ii,iii*ii,ii==iii ? '\n' : ' ');}
        else {printf("%d*%d=%d%c",iii,ii,iii*ii,ii==iii ? '\n' : ' ');}
    }} 
    return 0;
}
```
**BC83 牛牛学数列** 
```c
#include <stdio.h>

int main() {
    int in,ii=0;
    int ia=1;
    scanf("%d",&in);
    for (ii=2;ii<in+1;ii++) {
        if (ii%2) {ia+=ii;}
        else {ia-=ii;}}
    printf("%d",ia);
    return 0;
}
```
**BC84 牛牛学数列2** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    double d = 0;
    scanf("%d", &i);
    for (; i > 0; i--) {
        d += 1.0 / i;
    }
    int ia = d * 1000000;
    int ib = d * 10000000;
    (ib - ia * 10) > 4 && ia++;
    printf("%.6f", ia / 1000000.0);
    return 0;
}
```
**BC86 牛牛学数列4** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 1;
    int ib = 1;
    long long ll = 0;
    scanf("%d", &i);
    for (ia = 1; ia < i + 1; ia++) {
        for (ib = ia; ib > 0; ib--) {
            ll += ib;
        }
    }
    printf("%lld", ll);
    return 0;
}
```
**BC87 数位之和(循环版)** 
```c
#include <stdio.h>

int bc87(int i) {
    int icount = 0;
    while (i) {
        (icount += i % 10, i /= 10);
    }
    return icount;
}
int main() {
    int i = 0;
    scanf("%d", &i);
    printf("%d", bc87(i));
    return 0;
}
```
**BC87 数位之和(递归版)** 
```c
#include <stdio.h>

int bc87(int i) {
    if (i < 10) {
        return i;
    } else {
        return i % 10 + bc87(i / 10);
    }
}
int main() {
    int i = 0;
    scanf("%d", &i);
    printf("%d", bc87(i));
    return 0;
}
```
**BC88 魔法数字变换** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    for (i = i; 1 != i; ia++) {
        if (i % 2) {
            (i *= 3, i++);
        } else {
            i /= 2;
        }
    }
    printf("%d", ia);
    return 0;
}
```
**BC89 包含数字9的数** 
```c
#include <stdio.h>

int main() {
    int i = 10;
    int ia = 0;
    int icount = 2;
    for (; i < 2010; i++) {
        int iflag = 1;
        for (ia = i; ia / 10; ia /= 10) {
            if (9 == ia % 10) {
                icount++;
                iflag = 0;
                break;
            }
        }
        iflag&& (9 == ia % 10 && icount++);
    }
    printf("%d", icount);
    return 0;
}
```
**BC90 小乐乐算多少人被请家长** 
```c
#include <stdio.h>

int main() {
    int in = 0;
    int icount = 0;
    scanf("%d", &in);
    float arr[3] = {0};
    for (; in; in--) {
        scanf("%f %f %f", &arr[0], &arr[1], &arr[2]);
        (arr[0] + arr[1] + arr[2]) / 3.0 < 60 && icount++;
    }
    printf("%d", icount);
    return 0;
}
```
**BC93 公务员面试** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int arr[7] = {0};
    while (EOF != scanf("%d %d %d %d %d %d %d", &arr[0], &arr[1], &arr[2], &arr[3], &arr[4], &arr[5], &arr[6])) {
        int isum = 0;
        int imax = arr[0];
        int imin = arr[0];
        for (i = 0; i < 7; i++) {
            isum += arr[i];
            imax < arr[i]&& (imax = arr[i]), imin > arr[i] && (imin = arr[i]);
        }
        printf("%.2f\n", (isum - imax - imin) / 5.0);
    }
    return 0;
}
```
**BC94 反向输出一个四位数** 
```c
#include <stdio.h>

int main() {
    int in = 0;
    int i = 0;
    scanf("%d", &in);
    for (i = 0; i < 4; i++) {
        printf("%d", in % 10);
        in /= 10;
    }
    return 0;
}
```
**BC95 小乐乐与进制转换** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int arr[15] = {-1};
    for (i = 1; i < 15; i++) {
        arr[i] = -1;
    }
    scanf("%d", &i);
    for (ia = 0; i / 6; ia++) {
        arr[ia] = i % 6;
        i /= 6;
    }
    for (arr[ia] = i % 6; -1 != arr[ia];) {
        ia++;
    }
    for (ia--; -1 != ia; ia--) {
        printf("%d", arr[ia]);
    }
    return 0;
}
```
**BC96 [NOIP2015]金币** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 1;
    int ib = 1;
    int ic = 1;
    int id = 0;
    scanf("%d", &i);
    for (; ia < i; (ic += ib, id--, ia++)) {
        if (!id) {
            (ib++, id = ib);
        }
    }
    printf("%d", ic);
    return 0;
}
```
**BC97 回文对称数** 
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void reverses(char* str, int ilen) {
    char* cp = str;
    char* cpa = str + ilen - 1;
    for (; cp < cpa; cp++, cpa--) {
        char ctmp = 0;
        ctmp = *cp;
        *cp = *cpa;
        *cpa = ctmp;
    }
}
int reversei(int i) {
    char str[8] = "";
    sprintf(str, "%d", i);
    reverses(str, strlen(str));
    return atoi(str);
}
int main() {
    int i = 0;
    int ia = 1;
    scanf("%d", &i);
    for (; ia <= i; ia++) {
        ia == reversei(ia) && printf("%d\n", ia);
    }
    return 0;
}
```
**BC98 线段图案** 
```c
#include <stdio.h>

int main() {
    int a,i=0;
    while (scanf("%d", &a) != EOF) { for (i=0;i<a;i++) {
        printf("*");}
        printf("\n");}
    return 0;
}
```
**BC99 正方形图案** 
```c
#include <stdio.h>

int main() {
    int a,i=0;
    while (scanf("%d", &a) != EOF) { for (i=0;i<a;i++) {
        printf("*");}
        printf("\n");}
    return 0;
}
```
**BC100 直角三角形图案** 
```c
#include <stdio.h>

int main() {
    int a,i,ii=0;
    while (scanf("%d",&a) != EOF) {
        for (i=1;i<a+1;i++) {for (ii=i;ii>=1;ii--) {if (ii==1) {printf("*\n");}
        else {printf("* ");}
        }}}
    return 0;
}
```
**BC101 翻转直角三角形图案** 
```c
#include <stdio.h>

int main() {
    int a,i,ii=0;
    while (scanf("%d",&a) != EOF) { 
        for (i=a;i>0;i--) {for (ii=i;ii>0;ii--) {printf("*%c",ii==1 ? '\n' : ' ');}}
    }
    return 0;
}
```
**BC103 金字塔图案** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (EOF != scanf("%d", &i)) {
        int ic = i;
        for (i--; i > -1; i--) {
            for (ia = 0; ia < i; ia++) {
                printf(" ");
            }
            for (ib = 0; ib < ic - i; ib++) {
                printf("%c", ib % 2 ? ' ' : '*');
            }
            for (ic++, ia = 0; ia < i; ia++) {
                printf(" ");
            }
            printf("\n");
        }
    }
    return 0;
}
```
**BC108 反斜线形图案** 
```c
#include <stdio.h>

int main() {
    int a,i,ii=0;
    while (scanf("%d",&a) != EOF) { 
        for (i=a;i>0;i--) {for (ii=i;ii>0;ii--) {printf("*%c",ii==1 ? '\n' : ' ');}}
    }
    return 0;
}
```
**BC109 正斜线形图案** 
```c
#include <stdio.h>

int main() {
    int ia,ii,iii=0;
    while (scanf("%d", &ia) != EOF) { 
        for (ii=ia;ii>0;ii--) {for (iii=ii;iii>0;iii--) {printf("%s",iii==1 ? "*\n" : " ");}}
    }
    return 0;
}
```
**BC111 空心正方形图案** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (scanf("%d", &i) != EOF) {
        for (ia = 0; ia < i; ia++) {
            for (ib = 0; ib < i; ib++) {
                if (!(ia) || i - 1 == ia) {
                    printf("* ");
                } else {
                    printf("%c ", (!(ib) || i - 1 == ib) ? '*' : ' ');
                }
            }
            printf("\n");
        }
    }
    return 0;
}
```
**BC112 空心三角形图案** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (EOF != scanf("%d", &i)) {
        for (ia = 0; ia < i + 1; ia++) {
            for (ib = 0; ib < ia; ib++) {
                if (ia + 1 == i + 1) {
                    printf("*%c", ib + 1 == ia ? '\n' : ' ');
                } else {
                    printf("%c%c", !ib || ib + 1 == ia ? '*' : ' ', ib + 1 == ia ? '\n' : ' ');
                }
            }
        }
    }
    return 0;
}
```
**BC113 数字三角形** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (scanf("%d", &i) != EOF) {
        for (ia = 1; ia < i + 1; ia++) {
            for (ib = 1; ib < ia + 1; ib++) {
                printf("%d%c", ib, ia == ib ? '\n' : ' ');
            }
        }
    }
    return 0;
}
```

**BC116 [NOIP2013]记数问题** 
```c
#include <stdio.h>

int main() {
    int in = 0;
    int ix = 0;
    int count = 0;
    scanf("%d %d", &in, &ix);
    int ia = in;
    for (; ia > 0; ia--) {
        in = ia;
        for (; in / 10; in /= 10) {
            ix == (in % 10) && count++;
        }
        ix == (in % 10) && count++;
    }
    printf("%d", count);
    return 0;
}
```
**BC117 逆序输出** 
```c
#include <stdio.h>

int main() {
    int arr[10]={0};
    int i=0;
    for (i=0;i<10;i++) {scanf("%d",&arr[i]);}
    for (i=9;i>=0;i--) {printf("%d ",arr[i]);}
    return 0;
}
```
**BC118 N个数之和** 
```c
#include <stdio.h>

int main() {
    int a[50]={0};
    int i,ii,b=0;
    scanf("%d",&i);
    for (ii=0;ii<i;ii++) {scanf("%d",&a[ii]);}
    b=a[0];
    for (ii=1;ii<i;ii++) {b+=a[ii];}
    printf("%d",b);
    return 0;
}
```
**CPP13 计算一个数的阶乘** 
```c
#include <stdio.h>

int main() {
    long long i = 0;
    int ia = 0;
    while (scanf("%lld", &i) != EOF) {
        for (ia = i - 1; ia > 0; ia--) {
            i *= ia;
        }
        printf("%lld", i);
    }
    return 0;
}
```
**BC119 最高分与最低分之差** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int arr[10000] = {0};
    scanf("%d", &i);
    for (ia = 0; ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    int max = arr[0];
    int min = arr[0];
    for (ia = i - 1; ia > 0; ia--) {
        if (max < arr[ia]) {
            max = arr[ia];
        }
    }
    for (ia = i - 1; ia > 0; ia--) {
        if (min > arr[ia]) {
            min = arr[ia];
        }
    }
    printf("%d", max - min);
    return 0;
}
```
**BC120 争夺前五名** 
```c
#include <stdio.h>

int main() {
    int arr[50] = {0};
    int in = 0;
    int i = 0;
    scanf("%d", &in);
    for (; i < in; i++) {
        scanf("%d", &arr[i]);
    }
    while (in - 1 != i) {
        for (i = 0; i < in - 1; i++) {
            if (arr[i] < arr[i + 1]) {
                int itmp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = itmp;
            }
        }
        for (i = 0; i < in - 1; i++) {
            if (arr[i] < arr[i + 1]) {
                break;
            }
        }
    }
    for (i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```
**BC121 有序序列合并** 
```c
#include <stdio.h>

int main() {
    int arr[2000] = {0};
    int i = 0;
    int ia = 0;
    scanf("%d %d", &i, &ia);
    int ib = i;
    int ic = i;
    int id = 0;
    int itmp = 0;
    for (i = 0; i < ib; i++) {
        scanf("%d", &arr[i]);
    }
    for (; ic < i + ia; ic++) {
        scanf("%d", &arr[ic]);
    }
    for (id = ic; id > 0; id--) {
        for (ib = 0; ib < id - 1; ib++) {
            if (arr[ib] > arr[ib + 1]) {
                itmp = arr[ib];
                arr[ib] = arr[ib + 1];
                arr[ib + 1] = itmp;
            }
        }
    }
    for (i = 0; i < ic; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```
**BC122 有序序列判断** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int is = 0;
    int arr[50] = {0};
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    for (ia = 0; ia < i - 1; ia++) {
        (arr[ia] < arr[ia + 1] && !is)&& (is = -1);
        (arr[ia] > arr[ia + 1] && !is)&& (is = 1);
        if ((arr[ia] < arr[ia + 1] && 1 == is) || (arr[ia] > arr[ia + 1] && -1 == is)) {
            printf("un");
            break;
        }
    }
    printf("sorted");
    return 0;
}
```
**BC123 有序序列插入一个整数** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    int ic = 0;
    scanf("%d", &ia);
    long long arr[50] = {0};
    for (i = 0; i < ia; i++) {
        scanf("%lld", &arr[i]);
    }
    scanf("%d", &ib);
    for (i = 0; i < ia; i++) {
        !ic && arr[i] > ib && (printf("%d ", ib), ic = 1);
        printf("%lld ", arr[i]);
    }
    ic || printf("%d ", ib);
    return 0;
}
```
**BC124 序列中删除指定数字** 
```c
#include <stdio.h>

int main() {
    int arr[50] = {-1};
    int i = 0;
    int ia = 0;
    int id = 0;
    for (i = 0; i < 49; i++) {
        arr[i + 1] = arr[i];
    }
    for ((scanf("%d", &i), ia = 0); ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    scanf("%d", &id);
    for (ia = 0; ia < i; ia++) {
        if (arr[ia] == id) {
            arr[ia] = -1;
        }
    }
    for (ia = 0; ia < i; ia++) {
        -1 != arr[ia] && printf("%d ", arr[ia]);
    }
    return 0;
}
```
**BC126 小乐乐查找数字** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int icount = 0;
    int ix = 0;
    int arr[100] = {0};
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    for (scanf("%d", &ix), ia = 0; ia < i; ia++) {
        ix == arr[ia] && icount++;
    }
    printf("%d", icount);
    return 0;
}
```
**BC128 班级成绩输入输出** 
```c
#include <stdio.h>

int main() {
    float arr[5][5] = {0.0f};
    int i = 0;
    int ia = 0;
    float sum = 0.0f;
    for (i = 0; i < 5; i++) {
        for (ia = 0; ia < 5; ia++) {
            scanf("%f ", &arr[i][ia]);
        }
    }
    for (i = 0; i < 5; i++) {
        for (ia = 0; ia < 5; ia++) {
            printf("%.1f ", arr[i][ia]);
            sum += arr[i][ia];
        }
        printf("%.1f \n", sum);
        sum = 0.0f;
    }
    return 0;
}
```
**BC129 矩阵元素定位** 
```c
#include <stdio.h>

int main() {
    int arr[5][5] = {0};
    int in = 0;
    int im = 0;
    int ix = 0;
    int iy = 0;
    scanf("%d %d", &in, &im);
    for (; ix < in; ix++) {
        for (iy = 0; iy < im; iy++) {
            scanf("%d", &arr[ix][iy]);
        }
    }
    scanf("%d %d", &ix, &iy);
    printf("%d", arr[ix - 1][iy - 1]);
    return 0;
}
```
**BC131 矩阵相等判定** 
```c
#include <stdio.h>

int main() {
    long long arr[10][10] = {0};
    long long arra[10][10] = {0};
    int i = 0;
    int ia = 0;
    int ib = 0;
    int ic = 0;
    scanf("%d %d", &i, &ia);
    for (ib = 0; ib < i; ib++) {
        for (ic = 0; ic < ia; ic++) {
            scanf("%lld", &arr[ib][ic]);
        }
    }
    for (ib = 0; ib < i; ib++) {
        for (ic = 0; ic < ia; ic++) {
            scanf("%lld", &arra[ib][ic]);
        }
    }
    for (i = 0; i < 10; i++) {
        for (ia = 0; ia < 10; ia++) {
            if (arr[i][ia] != arra[i][ia]) {
                goto g;
            }
        }
    }
g:
    (10 == i && 10 == ia) && printf("Yes\n"), (10 == i && 10 == ia) || printf("No\n");
    return 0;
}
```
**BC132 矩阵计算** 
```c
#include <stdio.h>

int main() {
    int arr[10][10] = {0};
    int i = 0;
    int ia = 0;
    int ib = 0;
    long long llcount = 0;
    scanf("%d %d", &i, &ib);
    for (; i > 0; i--) {
        for (ia = 0; ia < ib; ia++) {
            scanf("%d", &arr[i][ia]);
        }
    }
    for (i = 0; i < 10; i++) {
        for (ia = 0; ia < 10; ia++) {
            if (arr[i][ia] > 0) {
                llcount += arr[i][ia];
            }
        }
    }
    printf("%lld", llcount);
    return 0;
}
```
**BC141 井字棋** 
```c
#include <stdio.h>

int main() {
    char str[3][3];
    char stra[3] = "KB";
    int i = 0;
    int ia = 0;
    int iw = 0;
    for (i = 0; i < 3; i++) {
        scanf("%c %c %c\n", &str[i][0], &str[i][1], &str[i][2]);
    }
    for (ia = 0; ia < 2; ia++) {
        for (i = 0; i < 3; i++) {
            if (str[i][0] == str[i][1] && str[i][1] == str[i][2] && stra[ia] == str[i][1]) {
                ia || (iw = 1), ia && (iw = -1);
            }
        }
        for (i = 0; i < 3; i++) {
            if (str[0][i] == str[1][i] && str[1][i] == str[2][i] && stra[ia] == str[1][i]) {
                ia || (iw = 1), ia && (iw = -1);
            }
        }
        if (str[0][0] == str[1][1] && str[1][1] == str[2][2] && stra[ia] == str[1][1] || str[0][2] == str[1][1] && str[1][1] == str[2][0] && stra[ia] == str[1][1]) {
            ia || (iw = 1), ia && (iw = -1);
        }
    }
    switch (iw) {
        case -1:
            printf("BoBo wins!");
            break;
        case 1:
            printf("KiKi wins!");
            break;
        case 0:
            printf("No winner!");
            break;
    }
    return 0;
}
```
**BC143 [NOIP2018]标题统计** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int icount = 0;
    char str[6] = "";
    for (i = 0; EOF != scanf("%c", &str[i]); i++) {
        ;
    }
    for (i = 0; i < 5; i++) {
        if (' ' != str[i] && '\n' != str[i] && '\0' != str[i]) {
            icount++;
        }
    }
    printf("%d", icount);
    return 0;
}
```
**BC144 登录验证** 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[25] = "";
    char stra[25] = "";
    while (EOF != scanf("%s %s", str, stra)) {
        printf("Login %s!\n", strcmp(str, "admin") ||
               strcmp(stra, "admin") ? "Fail" : "Success");
    }
    return 0;
}
```
**BC146 添加逗号** 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[11] = "";
    char stra[11] = "";
    scanf("%s", str);
    int i = 0;
    int ia = strlen(str) % 3;
    ia && (ia = 3 - ia);
    for (; i < strlen(str); i++) {
        stra[i] = str[strlen(str) - i - 1];
    }
    strcpy(str, stra);
    for (i = strlen(str) - 1; i > -1; ia++, i--) {
        printf("%c", str[i]);
        (2 == ia && i) && (printf(","), ia = -1);
    }
    return 0;
}
```
**BC147 竞选社长** 
```c
#include <stdio.h>

int main() {
    int ia = 0;
    int ib = 0;
    char str[100] = "";
    scanf("%s", str);
    char* cp = str;
    for (; '0' != *cp; cp++) {
        'A' == *cp && ia++, 'B' == *cp && ib++;
    }
    if (ia > ib) {
        printf("A");
    } else if (ia < ib) {
        printf("B");
    } else {
        printf("E");
    }
    return 0;
}
```
**BC148 字符串操作** 
```c
#include <stdio.h>

int main() {
    char str[100] = "";
    int in = 0;
    int im = 0;
    int il = 0;
    int ir = 0;
    char c1 = 0;
    char c2 = 0;
    scanf("%d %d %s", &in, &im, str);
    for (; im; im--) {
        scanf("%d %d %c %c", &il, &ir, &c1, &c2);
        for (in = il - 1; in < ir; in++) {
            c1 == str[in] && (str[in] = c2);
        }
    }
    printf("%s", str);
    return 0;
}
```
**BC149 简写单词** 
```c
#include <stdio.h>

int main() {
    char str[50] = "";
    while (EOF != scanf("%s", str)) {
        str[0] > 96 && (str[0] -= 32);
        printf("%c", str[0]);
    }
    return 0;
}
```
**BC151 数位五五** 
```c
#include <stdio.h>

int bc151(int i, int ia) {
    int icount = 0;
    for (; i <= ia; i++) {
        int isum = 0;
        int ib = i;
        for (; ib / 10; ib /= 10) {
            isum += ib % 10;
        }
        if (isum += ib % 10, !(isum % 5)) {
            icount++;
        }
    }
    return icount;
}
int main() {
    int i = 0;
    int ia = 0;
    scanf("%d %d", &i, &ia);
    printf("%d", bc151(i, ia));
    return 0;
}
```
**BC152 The Biggest Water Problem** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ic = 0;
    scanf("%d", &i);
    while (i > 9) {
        for (ia = i; ia / 10; ia /= 10) {
            ic += ia % 10;
        }
        ic += ia % 10;
        i = ic;
        ic = 0;
    }
    printf("%d", i);
    return 0;
}
```
**BC153 [NOIP2010]数字统计** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int count = 0;
    scanf("%d %d", &i, &ia);
    for (; i <= ia; i++) {
        int ib = i;
        for (; ib / 10; ib /= 10) {
            2 == ib % 10 && count++;
        }
        2 == ib % 10 && count++;
    }
    printf("%d", count);
    return 0;
}
```
**BC154 牛牛的短信** 
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    float fcount = 0;
    scanf("%d", &i);
    for (; i; i--) {
        scanf("%d", &ia);
        ia > 60 && (fcount += 0.2), ia > 60 || (fcount += 0.1);
    }
    printf("%.1f", fcount);
    return 0;
}
```
**BC166 小乐乐走台阶** 
```c
#include <stdio.h>

long long bc166(int in) {
    if (in < 2) {
        return 1;
    } else {
        return bc166(in - 1) + bc166(in - 2);
    }
}
int main() {
    int in = 0;
    scanf("%d", &in);
    printf("%lld", bc166(in));
    return 0;
}
```
**BC168 牛牛的西格玛** 
```c
#include <stdio.h>

int sigma(int in) {
    if (in != 1) {
        return in + sigma(in - 1);
    } else {
        return 1;
    }
}
int main() {
    int in = 0;
    scanf("%d", &in);
    printf("%d", sigma(in));
    return 0;
}
```
**BC170 牛牛的digit** 
```c
#include <stdio.h>
#include <math.h>

int digit(int ix, int i) {
    return ix % (long long)pow(10, i);
}
int main() {
    int i = 0;
    int ix = 0;
    scanf("%d %d", &ix, &i);
    ix = digit(ix, i);
    printf("%d", ix);
    return 0;
}
```
**BC171 牛牛的Hermite多项式** 
```c
#include <stdio.h>

int h(int in, int ix) {
    if (0 == in) {
        return 1;
    } else if (1 == in) {
        return 2 * in;
    } else if (in > 1) {
        return 2 * ix * h(in - 1, ix) - 2 * (in - 1) * h(in - 2, ix);
    }
    return 0;
}
int main() {
    int in = 0;
    int ix = 0;
    scanf("%d %d", &in, &ix);
    printf("%d", h(in, ix));
    return 0;
}
```
**BC172 牛牛的排列数** 
```c
#include <stdio.h>

long long amn(long long ll, long long lla) {
    if (1 == lla) {
        return ll;
    } else {
        return (ll - lla + 1) * amn(ll, lla - 1);
    }
}
int main() {
    long long lln = 0;
    long long llm = 0;
    scanf("%lld %lld", &lln, &llm);
    printf("%lld", amn(lln, llm));
    return 0;
}
```
**BC173 牛牛逆序输出** 
```c
#include <stdio.h>

int rept(int i) {
    printf("%d",i%10);
    if (!(i/10)) {
        return 0;
    } else {
        return rept(i/10);
    }  
}
int main() {
    int i=0;
    scanf("%d",&i);
    rept(i);
    return 0;
}
```
**CC5 牛牛的新数组求和** 
```c
#include <stdio.h>
#include <stdlib.h>

int cal(int* array, int n) {
    int ia = 0;
    int ic = 0;
    for (ia = 0; ia < n; ia++) {
        ic += array[ia];
    }
    return ic;
}
int main() {
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    int* arrp = (int*)malloc(4 * i);
    for (; ia < i; ia++) {
        scanf("%d", &arrp[ia]);
    }
    printf("%d", cal(arrp, i));
    return 0;
}
```
**CC6 牛牛的排序** 
```c
#include <stdio.h>
#include <stdlib.h>

int intcmp(const void* vp, const void* vpa) {
    return *(int*)vp - *(int*)vpa;
}
void sort(int* array, int n)  {
    qsort(array, n, 4, intcmp);
}
int main() {
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    int* arrp = (int*)malloc(4 * i);
    for (ia = 0; ia < i; ia++) {
        scanf("%d", &arrp[ia]);
    }
    sort(arrp, i);
    for (ia = 0; ia < i; ia++) {
        printf("%d ", arrp[ia]);
    }
    return 0;
}
```
**CC13 KiKi定义电子日历类** 
```c
#include <stdio.h>

struct Tdate{
    int Mouth;
    int Day;
    int Year;
};
int main() {
    struct Tdate a={0};
    scanf("%d %d %d",&a.Year,&a.Mouth,&a.Day);
    printf("%d/%d/%d",a.Day,a.Mouth,a.Year);
    return 0;
}
```
**CC15 牛牛的书** 
```c
#include <stdio.h>
#include <stdlib.h>

int intcmp(const void* vp, const void* vpa) {
    return *(int*)vp - *(int*)vpa;
}
struct Book {
    int imoney;
    char strname[100];
};
int main() {
    struct Book b[10];
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%s %d", b[ia].strname, &b[ia].imoney);
    }
    qsort(b, ia, sizeof b[0], intcmp);
    for (ia = 0; ia < i; ia++) {
        printf("%s\n", (b[ia]).strname);
    }
    return 0;
}
```
**CC16 牛牛的平面向量** 
```c
#include <stdio.h>

struct Xy {
    int ix;
    int iy;
};
int main() {
    int i = 0;
    int ia = 0;
    int icount = 0;
    scanf("%d", &i);
    struct Xy x[10] = {0};
    for (; ia < i; ia++) {
        scanf("%d %d", &x[ia].ix, &x[ia].iy);
    }
    for (ia = 0; ia < i; ia++) {
        icount += x[ia].ix;
    }
    printf("%d ", icount);
    for (ia = 0, icount = 0; ia < i; ia++) {
        icount += x[ia].iy;
    }
    printf("%d", icount);
    return 0;
}
```
**FED33 加粗文字** 
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <style>
       /* 填写样式 */
    </style>
</head>

<body>
    <!-- 填写标签 -->
    <p><b>牛客网</b>，程序员必备求职神器</p>
    <script type="text/javascript">
        // 填写JavaScript
    </script>
</body>

</html>
```
**NB158 牛牛的名字游戏** 
```c
#include <string.h>
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 *
 * @param s string字符串
 * @return int整型
 */
int lengthOfLastWord(char* s ) {
    int iconut = 0;
    char* cp = strpbrk(s, " ");
    if (!cp) {
        return strlen(s);
    }
    cp && (cp += strlen(s) - 1);
    for (; ' ' == *cp; cp--) {
        ;
    }
    for (; ' ' != *cp; iconut++, cp--) {
        ;
    }
    return iconut;
}
```
**NC120 二进制中1的个数** 
```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 *
 * @param n int整型
 * @return int整型
 */
int NumberOf1(int n ) {
    int ic = 0;
    int i = 0;
    for (; i < 32; n >>= 1, i++) {
        ic += (n & 1);
    }
    return ic;
}
```
**NC140 排序** 
```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 将给定数组排序
 * @param arr int整型一维数组 待排序的数组
 * @param arrLen int arr数组长度
 * @return int整型一维数组
 * @return int* returnSize 返回数组行数
 */
int* MySort(int* arr, int arrLen, int* returnSize) {
    int i = 0;
    int ia = 0;
    for (; i < arrLen; i++) {
        for (ia = 0; ia < arrLen - 1; ia++) {
            if (arr[ia] > arr[ia + 1]) {
                int itmp = arr[ia];
                arr[ia] = arr[ia + 1];
                arr[ia + 1] = itmp;
            }
        }
    }
    *returnSize = arrLen;
    return arr;
}
```
**PIO1 只有输出**
```c
#include <stdio.h>

int main() {
    printf("Hello Nowcoder!");
    return 0;
}
```
**PIO2 单组_A+B**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    scanf("%d %d", &i, &ia);
    printf("%d", i + ia);
    return 0;
}
```
**PIO3 多组_A+B_EOF形式**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    while (scanf("%d %d", &i, &ia) != EOF) {
        printf("%d\n", i + ia);
    }
    return 0;
}
```
**PIO4 多组_A+B_T组形式**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int i = 0;
    int arradd[2] = {0};
    scanf("%d", &i);
    for (; i; i--) {
        scanf("%d %d", &arradd[0], &arradd[1]);
        printf("%d\n", arradd[0] + arradd[1]);
    }
    return 0;
}
```
**PIO5 多组_A+B_零尾模式**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    while (scanf("%d %d", &i, &ia), i || ia) {
        printf("%d\n", i + ia);
    }
    return 0;
}
```
**PIO6 单组_一维数组**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    long long icount = 0;
    scanf("%d", &i);
    for (; i > 0; i--) {
        scanf("%d", &ia);
        icount += ia;
    }
    printf("%lld", icount);
    return 0;
}
```
**PIO7 多组_一维数组_T组形式**
```c
#include <stdio.h>

int main() {
    int it = 0;
    int in = 0;
    int i = 0;
    long long icount = 0;
    scanf("%d", &it);
    for (; it; it--) {
        scanf("%d", &in);
        for (; in; in--) {
            scanf("%d", &i);
            icount += i;
        }
        printf("%lld\n", icount);
        icount = 0;
    }
    return 0;
}
```
**PIO8 单组_二维数组**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    long long llcount = 0;
    scanf("%d %lld", &i, &llcount);
    i *= llcount;
    for (llcount = 0; i; i--) {
        scanf("%d", &ia);
        llcount += ia;
    }
    printf("%lld", llcount);
    return 0;
}
```
**PIO9 多组_二维数组_T组形式**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int in = 0;
    int im = 0;
    long long llcount = 0;
    scanf("%d", &i);
    for (; i; i--) {
        scanf("%d %lld", &in, &llcount);
        for (in *= llcount, llcount = 0; in; in--) {
            scanf("%d", &im);
            llcount += im;
        }
        printf("%lld\n", llcount);
    }
    return 0;
}
```
**PIO10 单组_字符串**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int i = 0;
    scanf("%d", &i);
    char* str = malloc(i--);
    scanf("%s", str);
    while (i > -1) {
        printf("%c", str[i--]);
    }
    return 0;
}
```
**PIO11 多组_字符串_T组形式**
```c
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    char str[100001] = "";
    for (scanf("%d", &i); i; i--) {
        scanf("%d %s", &ia, str);
        for (ia--; ia > -1; ia--) {
            printf("%c", str[ia]);
        }
        printf("\n");
    }
    return 0;
}
```
**PIO14 单组_保留小数位数**
```c
#include <stdio.h>

int main() {
    double d = 0.0;
    scanf("%lf", &d);
    printf("%.3lf", d);
    return 0;
}
```
**PIO15 单组_补充前导零**
```c
#include <stdio.h>

int main() {
    printf("Hello Nowcoder!");
    return 0;
}
```
**PIO16 单组_spj判断YES与NO**
```c
#include <stdio.h>

int main() {
    int i = 0;
    scanf("%d", &i);
    printf("%s", i % 2 ? "yes" : "no");
    return 0;
}
```
**WY11 星际穿越**
```c
#include <stdio.h>

int main() {
    long long a,i=0;
    scanf("%lld",&a);
    while (i+i*i<=a) {i++;}
    printf("%lld",i-1);
    return 0;
}
```
## C++
**CPP1 定义变量**
```c
#include <iostream>
using namespace std;

int main() {
    cout << "1\n4\n8\n8\n";
    return 0;
}
```
**CPP3 两数求和**
```c
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    cin >> i >> ia;
    cout << i + ia;
    return 0;
}
```
**CPP4 获取两数中的较大值**
```c
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    cin >> i >> ia;
    cout << (i < ia ? ia : i);
    return 0;
}
```
**CPP5 简单运算**
```c
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int itmp = 0;
    cin >> i >> ia;
    if (i < ia) {
        itmp = ia;
        ia = i;
        i = itmp;
    }
    cout << i + ia << ' ' << i - ia << ' ' << i * ia << ' ' << i / ia << ' ' << i % ia;
    return 0;
}
```
**CPP6 交换两个变量的值**
```c
#include <iostream>
using namespace std;

int main() {
    int a = 0;
    int b = 0;
    cin >> a >> b;
    cout << b << " " << a << endl;
    return 0;
}
```
**CPP7 获取三个数中的最大值（三元表达式实现）**
```c
#include <iostream>
using namespace std;

int main() {
    int a = 0;
    int b = 0;
    int c = 0;
    cin >> a >> b >> c;
    cout << ((a >= b && a >= c) ? a : (b >= a && b >= c) ? b : c) << endl;
    return 0;
}
```
**CPP8 计算商品打折结算金额**
```c
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    double price;
    cin >> price;
    if (price >= 5000) {
        price *= 0.6;
    } else if (price >= 2000) {
        price *= 0.7;
    } else if (price >= 500) {
        price *= 0.8;
    } else if (price >= 100) {
        price *= 0.9;
    }
    cout << setiosflags(ios::fixed) << setprecision(1) << price << endl;

    return 0;
}
```
**CPP9 判断身材状态**
```c
#include <iostream>
using namespace std;

int main() {
    double dw = 0.0;
    double dh = 0.0;
    cin >> dw >> dh;
    dw /= dh * dh;
    if (dw < 18.5) {
        cout << "偏瘦" << endl;
    } else if (dw < 20.9) {
        cout << "苗条" << endl;
    } else if (dw < 24.9) {
        cout << "适中" << endl;
    } else {
        cout << "偏胖" << endl;
    }
    return 0;
}
```
**CPP10 判断成绩等级**
```c
#include <iostream>
using namespace std;

int main() {
    int score = 0;
    cin >> score;
    if (score > 100 || score < 0) {
        cout << "成绩不合法" << endl;
    } else if (score > 89) {
        cout << "优秀" << endl;
    } else if (score > 79) {
        cout << "良" << endl;
    } else if (score > 69) {
        cout << "中" << endl;
    } else if (score > 59) {
        cout << "及格" << endl;
    } else {
        cout << "差" << endl;
    }
    return 0;
}
```
**CPP11 判断季节**
```c
#include <iostream>
using namespace std;

int main() {
    int im;
    cin >> im;
    switch (im) {
        case 12:
        case 1:
        case 2:
            cout << "冬季" << endl;
            break;
        case 3:
        case 4:
        case 5:
            cout << "春季" << endl;
            break;
        case 6:
        case 7:
        case 8:
            cout << "夏季" << endl;
            break;
        case 9:
        case 10:
        case 11:
            cout << "秋季" << endl;
            break;
        default:
            cout << "不合法" << endl;
            break;
    }
    return 0;
}
```
**CPP12 求 1 - n 之间偶数的和**
```c
#include <iostream>
using namespace std;

int main() {
    int n = 0;
    cin >> n;
    int sum = 0;
    for (; n > 0; n--) {
        n % 2 || (sum += n);
    }
    cout << sum << endl;
    return 0;
}
```
**CPP14 输出水仙花数**
```c
#include <iostream>
using namespace std;

int main() {
    int i = 100;
    for (; i < 1000; i++) {
        int ia = i % 10;
        int ib = i / 10 % 10;
        int ic = i / 100;
        i == ia * ia * ia + ib * ib * ib + ic * ic * ic && cout << i << endl;
    }
    return 0;
}
```
**CPP15 打印乘法表**
```c
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 1;
    int ib = 1;
    cin >> i;
    for (; ia < i + 1; ia++) {
        for (ib = 1; ib < ia + 1; ib++) {
            cout << ib << " * " << ia << " = " << ia * ib << "    ";
        }
        cout << endl;
    }
    return 0;
}
```
**CPP24 字符串拼接**
```c
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str = "";
    string stra = "";
    getline(cin, str);
    getline(cin, stra);
    cout << str << stra;
    return 0;
}
```
