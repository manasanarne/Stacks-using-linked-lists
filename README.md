# Stacks-using-linked-lists
#include<stdio.h>
#include<stdlib.h>
struct slist
{
        int data;
        struct slist *next;
};
typedef struct slist node;
node *s=NULL;
void push(int x)
{
        node *new;
        new=(node *)malloc(sizeof(node));
        new->data=x;
        new->next=NULL;
        if(s==NULL)
        {
                s=new;
        }
        else
        {
                new->next=s;
                s=new;
        }
}
int pop()
{
        node *temp;
        int x;
        if(s==NULL)
        {
                return -1;
        }
        else
        {
                temp=s;
                x=temp->data;
                s=s->next;
                free(temp);
                return x;
        }
}
int peek()
{
        return s->data;
}
void display()
{
        node *temp;
        if(s==NULL)
        {
                printf("No stack found\n");
        }
        else
        {
                temp=s;
                while(temp!=NULL)
                {
                        printf("%d->",temp->data);
                        temp=temp->next;
                }
                printf("NULL\n");
        }
}
void main()
{
        int x,ch;
        printf("Menu Driven\n1.Push\n2.Pop\n3.Peek\n4.Display\n5.Exit\n");
        while(1)
        {
                printf("Enter your choice\n");
                scanf("%d",&ch);
                switch(ch)
                {
                        case 1:printf("Enter a value to push\n");
                               scanf("%d",&x);
                               push(x);
                               break;
                        case 2:x=pop();
                               if(x==-1)
                               {
                                       printf("Stack Under Flow\n");
                               }
                               else
                               {
                                       printf("The pop item is %d\n",x);
                               }
                               break;
                        case 3:x=peek();
                               printf("The peek element is %d\n",x);
                               break;
                        case 4:display();
                               break;
                        case 5:printf("While loop is terminated\n");
                               exit(0);
                        default:printf("Check Your Choice\n");
                }
        }
}
