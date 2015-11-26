title: ACM解题报告之 hdu5137 How Many Maos Does the Guanxi Worth(ACM/ICPC 西安区域赛现场赛)
date: 2015-11-25 13:23:25
tags: [acm,ACM/ICPC西安区域赛现场赛]
categories: acm解题报告
keywords: acm
---
# How Many Maos Does the Guanxi Worth
>Time Limit: 2000/1000 MS (Java/Others)    Memory Limit: 512000/512000 K 
>Total Submission(s): 1371  
>Accepted Submission(s): 510

Problem Description:
-------------------
>"Guanxi" is a very important word in Chinese. It kind of means "relationship" or "contact". Guanxi can be based on friendship, but also can be built on money. So Chinese often say "I don't have one mao (0.1 RMB) guanxi with you." or "The guanxi between them is naked money guanxi." It is said that the Chinese society is a guanxi society, so you can see guanxi plays a very important role in many things.

>Here is an example. In many cities in China, the government prohibit the middle school entrance examinations in order to relief studying burden of primary school students. Because there is no clear and strict standard of entrance, someone may make their children enter good middle schools through guanxis. Boss Liu wants to send his kid to a middle school by guanxi this year. So he find out his guanxi net. Boss Liu's guanxi net consists of N people including Boss Liu and the schoolmaster. In this net, two persons who has a guanxi between them can help each other. Because Boss Liu is a big money(In Chinese English, A "big money" means one who has a lot of money) and has little friends, his guanxi net is a naked money guanxi net -- it means that if there is a guanxi between A and B and A helps B, A must get paid. Through his guanxi net, Boss Liu may ask A to help him, then A may ask B for help, and then B may ask C for help ...... If the request finally reaches the schoolmaster, Boss Liu's kid will be accepted by the middle school. Of course, all helpers including the schoolmaster are paid by Boss Liu.

<!--more-->

>You hate Boss Liu and you want to undermine Boss Liu's plan. All you can do is to persuade ONE person in Boss Liu's guanxi net to reject any request. This person can be any one, but can't be Boss Liu or the schoolmaster. If you can't make Boss Liu fail, you want Boss Liu to spend as much money as possible. You should figure out that after you have done your best, how much at least must Boss Liu spend to get what he wants. Please note that if you do nothing, Boss Liu will definitely succeed.
 
## Input:

>There are several test cases.

>For each test case:

>The first line contains two integers N and M. N means that there are N people in Boss Liu's guanxi net. They are numbered from 1 to N. Boss Liu is No. 1 and the schoolmaster is No. N. M means that there are M guanxis in Boss Liu's guanxi net. (3 <=N <= 30, 3 <= M <= 1000)

>Then M lines follow. Each line contains three integers A, B and C, meaning that there is a guanxi between A and B, and if A asks B or B asks A for help, the helper will be paid C RMB by Boss Liu.

>The input ends with N = 0 and M = 0.

>It's guaranteed that Boss Liu's request can reach the schoolmaster if you do not try to undermine his plan.

----
## Output:

>For each test case, output the minimum money Boss Liu has to spend after you have done your best. If Boss Liu will fail to send his kid to the middle school, print "Inf" instead.
 

## Sample Input:
>4 5

>1 2 3

>1 3 7

>1 4 50

>2 3 4

>3 4 2

>3 2

>1 2 30

>2 3 10

>0 0

---
## Sample Output
>50

>Inf
 

## Source
>2014ACM/ICPC亚洲区广州站-重现赛（感谢华工和北大）

## 题目大意:
>给定N个点和M条边，点编号是1到N。现在要从2到N-1中选择一个删除，同时跟选择的点连接的边也就消失，然后使得点1到N的最短路径的长度最大。如果点1和点N不连通，则输出“Inf"。

## 解题思路:
>暴力+floyd即可.

## AC代码:

    #include<iostream>
    #include<cstring>
    #include<algorithm>
    #include<cstdio>
    using namespace std;

    //path[i][j] = j;
    
    const int maxn = 40;
    int path[maxn][maxn],graph[maxn][maxn];
    int temp[maxn][maxn];
    const int inf = 0x3f3f3f3f;
    int m;
    
    void floyd()
    {
        int i,j,k;
    	for(k=1;k<=m;k++)
    	{
    		for(i=1;i<=m;i++)
    		{
    			for(j=1;j<=m;j++)
    			{
    				if((temp[i][k] == inf) || (temp[k][j] == inf)) continue;
    				if((temp[i][j] == inf) || (temp[i][j] > temp[i][k] + temp[k][j]))
    				{
    					temp[i][j] = temp[i][k] + temp[k][j];
    					//cout<<temp[i][j]<<endl;
    					path[i][j] = k;
    					//cout<<temp[i][j]<<endl;
    				}
    			}
    		}
    	}
    }
    
    int main()
    {
    	int n;
    	int num1,num2,num3;
    	int Min,Max;
    	int i,j;
    	//freopen("1.txt","r",stdin);
    	while(scanf("%d%d",&m,&n) != EOF && (m || n))
    	{
    		Max = -10000;
    		memset(path,inf,sizeof(path));
    		for(i=1;i<=m;i++)
    		{
    			for(j=1;j<=m;j++)
    			{
    				graph[i][j] = (i == j) ? 0 : inf;
    			}
    		}
    		memset(temp,inf,sizeof(temp));
    		for(i=0;i<n;i++)
    		{
    			scanf("%d%d%d",&num1,&num2,&num3);
    			if(graph[num1][num2] > num3)
    			{
    				graph[num1][num2] = num3;
    				graph[num2][num1] = num3;
    				temp[num1][num2] = num3;
    				temp[num2][num1] = num3;
    			}
    		}
    		int ci,bi;
    		for(i=2;i<m;i++) //枚举删除每个点 
    		{
    			for(j=1;j<=m;j++)
    			{
    				if(graph[i][j] != inf && i != j)
    				{
    					temp[i][j] = inf;
    					temp[j][i] = inf;
    				}
    			}
    			floyd();
    			//Max = max(Max,floyd());
    			Min = temp[1][m];
    			//cout<<":::"<<Min<<endl;
    			memset(temp,inf,sizeof(temp));
    			memset(path,inf,sizeof(path));
    			for(ci=1;ci<=m;ci++)
    			{
    				for(bi=1;bi<=m;bi++)
    				{
    					temp[ci][bi] = graph[ci][bi];
    				}
    			}
    			Max = max(Max,Min);
    		}
    		if(Max == inf)
    		{
    			printf("Inf\n");
    		}
    		else
    			printf("%d\n",Max);
    	}
    	return 0;
    }
