---
title: 员工排序
date: 2022-05-09 19:08:31
categories: c/c++
tags:
- 算法
- c/c++
---

#### 题目

某公司要针对员工情况统一调薪，现有一个员工列表，包含姓名、职级、工作年限、工资信息。现要求将该列表按以下规则重新排序：

<!-- more -->

1、职级高的排在前面

2、若职级相同，按工资少的排前面

3、若工资相同，工作年限长的排前面

**输入描述**：

第一行输入一个整数n，表示员工列表中员工的人数

接下来的n行，分别输入员工的姓名、职级、工作年限和工资信息，各项信息用空格分隔

**输出描述**：

输出按要求重新排列的员工列表，每名员工信息（姓名、职级、工作年限和工资）占一行

#### 示例

**示例1**：

```
6
张三 3 3 3000
李四 3 4 3000
王五 3 3 4000
赵六 4 3 3000
陆奇 4 4 4000
闫八 4 4 3980.99
```

**输出**：

```
赵六 4 3 3000.00
闫八 4 4 3980.99
陆奇 4 4 4000.00
李四 3 4 3000.00
张三 3 3 3000.00
王五 3 3 4000.00
```

#### 分析

1. 员工有多个信息，因此想到用结构体作为员工类型；
2. 由于员工数是不确定的，可以想到采用链表的数据结构，但是链表无法通过下标访问，排序效率低，题目所求需要排序，所以不应用链表，还是采用数组，不过是动态创建数组，使用`malloc`或`calloc`函数，需要包含库文件`<stdlib.h>`；
3. 再看题目，表面上是要我们作出排序，其实员工的信息我们是采用数组存放的，可以直接通过下标访问，因此我们没必要真的对员工进行排序，只需要按照顺序记录他们的下标即可，通过另外的数组存储下标，然后按顺序访问该数组的元素，即可得到排好序的员工信息，有了思路，代码就好写了；
4. 这里需要注意的是，每找到一个员工，需要将他从原数组中排除，即后续的寻找中不应再有该员工的信息出现，因此需要另加一个函数判断此员工下标是否在已排好序的数组中，同时，每次循环时，数组当前下标存放的信息每次都需要更新，不能存放已排好序的员工信息的下标。

#### 代码

```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <math.h>

typedef struct Worker
{
	char name[20];
	int state;
	int workAge;
	double wage;

} Worker;

Worker *init(int num);
int *sortWorker(int num, Worker *worker);
bool isIn(int a, const int *p, int num);

int main(void)
{
	int num = 0;
	Worker *worker = NULL;
	int *array = NULL;
	scanf("%d", &num);

	//³õÊ¼»¯
	worker = init(num);
	if (worker == NULL)
	{
		printf("ÉêÇë¿Õ¼äÊ§°Ü\n");
		exit(0);
	}
	for (int i = 0; i < num; i++)
	{
		scanf("%s %d %d %lf", worker[i].name, &worker[i].state, &worker[i].workAge, &worker[i].wage);
	}

	array = sortWorker(num, worker);

	for (int i = 0; i < num; i++)
	{
		printf("%s %d %d %.2f\n", worker[array[i]].name, worker[array[i]].state,
			   worker[array[i]].workAge, worker[array[i]].wage);
	}

	free(worker);
	free(array);

	getchar();

	return 0;
}

Worker *init(int num)
{
	Worker *worker = (Worker *)malloc(sizeof(Worker) * num);

	return worker;
}

int *sortWorker(int num, Worker *worker)
{
	Worker w = worker[0];
	int *label = (int *)malloc(sizeof(int) * num);
	int count = 0;
	label[count] = 0;

	for (; count < num; count++)
	{

		for (int i = 0; i < num; i++)
		{
			if (!isIn(i, label, count))
			{
				if (w.state == worker[i].state)
				{
					if (fabs(w.wage - worker[i].wage) < 1e-10)
					{
						if (w.workAge < worker[i].workAge)
						{
							w = worker[i];
							label[count] = i;
						}
					}
					else
					{
						if (w.wage > worker[i].wage)
						{
							w = worker[i];
							label[count] = i;
						}
					}
				}
				else
				{
					if (w.state < worker[i].state)
					{
						w = worker[i];
						label[count] = i;
					}
				}
			}
		}

		for (int i = 0; i < num; i++)
		{
			if (!isIn(i, label, count))
			{
				w = worker[i];
				label[count + 1] = i;
			}
		}
	}

	return label;
}

bool isIn(int a, const int *p, int num)
{
	for (int i = 0; i <= num; i++)
	{
		if (a == p[i])
		{
			return true;
		}
	}

	return false;
}
```

