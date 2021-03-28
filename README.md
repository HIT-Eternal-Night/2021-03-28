# 2021-03-28
穷举与递推的代码训练

1：魔术师猜数问题
#include<stdio.h>

int main(int argc,char const*argv[])
{
	int n;
	int sum;
	int a,b,c;
	int find = 0;
	printf("Input a sum:");
	scanf("%d",&sum);
	
	for (n=100 ; n<1000 && !find ; n++)
	{
		a = n / 100;
		b = n % 100 / 10;
		c = n % 10;
		if (a*100+c*10+b+b*100+a*10+c+b*100+c*10+a+c*100+a*10+b+c*100+b*10+a == sum)
		{
			printf("The number is %d\n",a*100+b*10+c);
			find = 1;
		}
	}
	
	if (find == 0)
	{
		printf("The sum you calculated is wrong!\n");
	}
	
	return 0;
}

2：三色球问题
#include<stdio.h>

int main(int argc,char const*argv[])
{
	int i,j,k;
	const int AMOUNT  =  8;
	
	for (i=0 ; i<=3 ; i++)
	{
		for (j=0 ; j<=3 ; j++)
		{
			for (k=0 ; k<=6 ; k++)
			{
				if (i+j+k == AMOUNT)
				{
					printf("i=%d, j=%d, k=%d\n",i,j,k);
				}
			}
		}
	} 
	return 0;
}

3：猴子吃桃问题
#include<stdio.h>

int MonkeyEatPeach(int days);

int main(int argc,char const*argv[])
{
	int    x;
	int days;
	
	printf("Input days:\n");
	scanf("%d",&days);
	
	x = MonkeyEatPeach(days);
	printf("x=%d\n",x);
	
	return 0;
}

int MonkeyEatPeach(int days)
{
	int x = 1;
	while (days > 1)
	{
		x = 2 * (x + 1);
		days--;
	}
	return x;
}

4：除不尽的自然数
#include<stdio.h>

int main(int argc,char const*argv[])
{
	int x;
	int a;
	
	for (x=0 ; ; x++)
	{
		if (x%8 == 1 && x/8%8 == 1 && x/8/8%8 == 7)
		{
			a = x/8/8/8;
		}
		
		if (x%17 == 4 && x/17%17 == 15 && x/17/17 == a*2)
		{
			printf("The required number is :%d\n",x);
			break;
		}
	}
	
	return 0;
}
总结：单层循环的break要放在if内。本题不能分别记录a1,a2,
然后if(a2 == 2*a1) (即用3个if)。这无法保证a1,a2对应同一个x值

5：打印200~300之间所有素数
#include<stdio.h>

int fun(int m);

int main(int argc,char const*argv[])
{
	int n;
	for (n=200 ; n<=300 ; n++)
	{
		if (fun(n))
		printf("%d\n",n);
	}
	return 0;
}

int fun(int m)
{
	if (m <= 1)
	{
		return 0;
	}
	else
	{
		int i;
		for (i=2 ; i<m ; i++)
		{
			if (m % i == 0)
			return 0;
		}		
		return 1;
	}
}

6:减式还原
#include<stdio.h>

int main(int argc,char const*argv[])
{
	int P,E,A,R;
	
	for (P=1 ; P<10 ; P++)
	{
		for (E=0 ; E<10 ; E++)
		{
			for (A=0 ; A<10 ; A++)
			{
				for (R=0 ; R<10 ; R++)
				{
					if ((P*1000+E*100+A*10+R) - (A*100+R*10+A) == (P*100+E*10+A))
					{
						printf("    PEAR        %d%d%d%d\n",P,E,A,R);
						printf("     ARA       - %d%d%d\n",  A,R,A);
						printf("-----------   ----------------\n"  );
						printf("     PEA         %d%d%d\n", P,E,A);
						goto out;
					}
				}
			}
		}
	}
out: 
	return 0;
}

7：马克思手稿中的数学问题
#include<stdio.h>
#define TOTAL 30

int main(int argc,char const*argv[])
{
	int man,woman,kid;
	int count = 0;
	const int MONEY = 50;

	printf("\tMEN\tWOMEN\tCHILDREN\n");
	printf("-----------------------------------------\n");
	for(man=0;man<=TOTAL;man++)
	{
		for(woman=0;woman<=TOTAL;woman++)
		{
			for(kid=0;kid<=TOTAL;kid++)
			{			
					if(((man*3 + woman*2 + kid*1) == MONEY) &&
					(man + woman + kid == TOTAL))
					{
						count ++;
						printf("%2d:\t%d\t%d\t%d\n",count,man,woman,kid);
					}
			}
		}
	}
	return 0;
}

8：输出1-100之间能被3整除却不能被7整除的所有整数之和
#include<stdio.h>

int main(int argc,char const*argv[])
{
	int i;
	int sum = 0;
	
	for (i=1 ; i<=100 ; i++)
	{
		if (i%3 == 0 && i%7 != 0)
		{
			sum += i;
		}
	}
	
	printf("sum=%d\n",sum);
	return 0;
}

9：捕鱼分鱼
#include <stdio.h>
#include <stdlib.h>
 
int TakeFish(int n);
 
int main(int argc,char const*argv[])
{
    int total;
    total = TakeFish(5);
    printf("The total number of fish is:%d\n",total);
    return 0;
}
 
int TakeFish(int n)
{
	static int i=0;
	
	if(n==1)
	{
		do
		{
			i++;
		} while (i % 5 != 0);
		return (i+1);
		
	}
	else
	{
		int a;
		do
		{
			a = TakeFish(n-1);
		} while (a % 4 != 0);
		return (a / 4 * 5 + 1);
	}
}

10:通分比较分数大小
#include <stdio.h>
 
int LCM(int a, int b);

int main(int argc,char const*argv[])
{
	int a,b,c,d;
	int lcm; 
	
	printf("Input two fractions\n");
	scanf("%d/%d,%d/%d",&a,&b,&c,&d);
	
	lcm = LCM(b,d);
	//printf("%d\n",lcm);
	if (a*(lcm/b) == c*(lcm/d))
	{
		printf("%d/%d=%d/%d\n",a,b,c,d);
	}
	else if (a*(lcm/b) > c*(lcm/d))
	{
		printf("%d/%d>%d/%d\n",a,b,c,d);
	}
	else
	{
		printf("%d/%d<%d/%d\n",a,b,c,d);
	}
	return 0;
}

int LCM(int a, int b)
{
	int i;
	for (i=a>b?a:b ; ; i++)
	{
		if (i%a == 0 && i%b == 0)
		return i;
	} 
}
