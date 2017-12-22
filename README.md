# huang
#include<stdio.h>
#include<stdlib.h>
#include<Windows.h>
int result[100][1000000];
int count = 0;
int num1[100][1];
void  main() {
	int flag = 0, flag1;
	while (flag == 0)
	{
		printf("欢迎进入黄金点游戏\n");
		int i, a, j;
		int num[1000], sum = 0, l, m, G, num2[1000], num3[100], num4[100], t;
		printf("请输入本轮参加游戏的人数\n");
		scanf("%d", &a);//玩家人数
		for (i = 0; i < a; i++)//输入各个玩家的数据
		{
			printf("请第%d成员输入数据",i+1);
			scanf("%d", &num[i]);
			if (num[i]<0)
			{
				exit(0);
			}
			else
			{
				if (num[i]>100)
				{
					exit(0);
				}
			}
		}
		for (i = 0; i < a; i++)
		{
			l = num[i];
			sum = sum + l;
		}
		G = (int)(sum / a*0.618);//G值
		for (i = 0; i < a; i++)
		{
			l = abs(num[i]-G);
			num2[i] = l;
			num3[i] = l;
		}
		for (i = 1; i < a; i++)//冒泡排序
		{
			for (j = 0; j < a - 1; j++)
			{
				if (num3[j] > num3[j + 1])
				{
					t = num3[j];
					num3[j] = num3[j + 1];
					num3[j + 1] = t;
				}
			}
		}
		for (i = 0; i < a; i++)//num4=0
		{
			num4[i] = 0;
		}
		for (i = 0; i < a; i++)
		{
			l = num3[0], m = num3[a - 1];
			if (num2[i] == l)
			{
				num4[i] = a;
			}
			if (num2[i] == m)
			{
				num4[i] = -2;
			}
		}

		for (i = 0; i < a; i++)//输出各个玩家的信息
		{
			printf("第%d个成员的成绩为%d\n",i+1, num4[i]);
		}
		for (i = 0; i < a; i++)
		{
			result[count][i] = num4[i];
		}
		num1[count][0] = a;
		count++;
		printf("是否还想继续,是请按0，否请按任意键退出游戏");
		scanf("%d", &flag);
	}
	int n, i;
	printf("请问是否想查看之前的成绩，是请输入0，否按任意键退出\n");
	scanf("%d", &flag1);
	while (flag1 == 0)//查看各轮结果的比赛成绩
	{
		printf("请输入想查看的第几轮成绩");
		scanf("%d", &n);
		for (i = 0; i<num1[n - 1][0]; i++)
		{
			printf("第%d个成员的成绩为%d\n",i+1, result[n - 1][i]);
		}
		printf("是否还要继续观看，是请输入0，否按任意键退出\n");
		scanf("%d", &flag1);
	}
	system("pause");
}
