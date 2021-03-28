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

3：
