# huang
#include <stdio.h>
#include <math.h>
void main()
{
int i,n,j,k;
char s='Y';
int a=0;
int maxscore;
int student[50];
int number[50];
double b=0;
double min = 100 , max = 0;
while(s=='Y')
{ 
maxscore=-1000;
printf("请输入游戏人数："); 
scanf("%d",&n);
printf("请输入游戏局数：");
scanf("%d",&j);
for(i=0;i<n;i++) //将得分数组赋值0
{
student[i]=0;
}
for(k=0;k<j;k++) //局数循环
{
for(i=1;i<=n;i++) //输入每个同学的数并求和
{
printf("请输入第%d个人的数字：",i);
scanf("%d",&number[i-1]);
a += number[i-1];
}

printf("G值为：%.3f \n",b=a/n*0.618); //输出G值
for(i=0;i<n;i++) 
{
if(fabs(number[i]-b)<min) //用每个数分别减去G值并取绝对值找到最大绝对值max与最小min
{
min=fabs(number[i]-b);
}
}
for(i=0;i<n;i++)
{
if(fabs(number[i]-b)>max)
{
max=fabs(number[i]-b);
}
}
for(i=0;i<n;i++) //通过max与min找到距离G点最远与最近的数，并将对用同学的成绩进行修改
{
if(fabs(number[i]-b)==min)
{

if(fabs(number[i]-b)==max)
{	student[i]=student[i]+n;
}
student[i]-= 2;
}
}
a=0; //每轮游戏结束将一些必要数值重置
b=0;
max=0;
min=100;
printf("*******************************\n");
for(i=0;i<n;i++) //打印出每个同学成绩
{
printf("*第%d位学生的得分为%d\n",i+1,student[i]);
}
printf("*******************************\n");
}
for(i=0;i<n;i++) //找到最高分
{
if(student[i]>maxscore)
{
maxscore=student[i];
}
}


printf("游戏结束！结果如下：\n");

printf("恭喜得数为%d的同学获胜！\n",maxscore); //输出游戏结果
printf("____________________________________________________________________\n");
printf("是否继续游戏？ Y/N\n"); //游戏结束判断是否继续游戏
scanf("%s",&s);
}

}
