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

