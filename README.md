# test_9_29
#include <stdio.h>
#include <stdlib.h>
#define MaxSize 50
typedef struct{
	int data[MaxSize];
	int front,rear;
}SqQueue;

void InitQueue(SqQueue &Q){
	Q.front = Q.rear = 0;
}
bool QueueEmpty(SqQueue Q){
	if(Q.front == Q.rear)
		return true;
	else
		return false;
}
bool EnQueue(SqQueue &Q,int x){
	if((Q.rear+1)% MaxSize == Q.front)
		return false;
	Q.data[Q.rear] = x;
	Q.rear = (Q.rear+1)% MaxSize;
	return true;
}
bool DeQueue(SqQueue &Q,int &x){
	if(Q.front == Q.rear)
		return false;
	x = Q.data[Q.front];
	Q.front = (Q.front+1)% MaxSize;
	return true;
}
bool GetHead(SqQueue Q,int &x){
	if(Q.front == Q.rear)
		return false;
	x = Q.data[Q.front];
	return true;
}

typedef struct{
	int data[MaxSize];
	int front,rear;
	int size;//int tag;
}SqQueue;
void testQueue(){
	SqQueue Q;
	InitQueue(&Q);
	QueueEmpty(Q);
	EnQueue(&Q,x);
	DeQueue(&Q,&x);
	GetHead(Q,&x);
}
//链式存储
typedef struct LinkNode{
	int data;
	struct LinkNode* next;
}LinkNode;
typedef struct{
	LinkNode *front,*rear;
}LinkQueue;
//带头结点
void InitQueue(LinkQueue &Q){
	Q.front = Q.rear = (LinkNode*)malloc(sizeof(LinkNode));
	Q.front->next = NULL;
}
//不带头结点
void InitQueue(LinkQueue &Q){
	Q.front = NULL;
	Q.rear = NULL;
}
bool IsEmpty(SqQueue Q){
	if(Q.front == Q.rear)
		return true;
	else
		return false;
}
