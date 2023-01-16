哈希表（hash table）

定义

typedef struct HashList

{

int num;

char* data;

}HashList;

例子

#include<stdio.h>
#include<stdlib.h>
typedef struct HashList
{
	int num;
	char* data;
}HashList;
HashList* initList()
{
	HashList* list=(HashList*)malloc(sizeof(HashList));
	list->num=0;
	list->data=(char*)malloc(sizeof(char)*5);
	for(int i=0;i<10;i++)
	{
		list->data[i]=0;
	}
	return list;
} 
int Hash(char data)
{
	return data%5;
}
void Put(HashList* list,char data)
{
	int index=Hash(data);
	if(list->data!=0)
	{
		int count=1;
		while(list->data[index]!=0)
		{
			index=Hash(Hash(data)+count);
			count++;
		}
	}
	list->data[index]=data;
	return;
}
int main()
{
	HashList* list=initList();
	Put(list,'A');
	Put(list,'F');
	printf("%c\n",list->data[0]);//A
	printf("%c\n",list->data[1]);//F
	return 0;
}