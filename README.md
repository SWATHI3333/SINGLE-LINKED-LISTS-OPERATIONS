# SINGLE-LINKED-LISTS-OPERATIONS
#include <stdio.h>
#include <stdlib.h>
struct slist
{
    int data;
    struct slist *next;
};
typedef struct slist node;
node * create(node *first)
{
    node *new,*prev;
    int x;
    printf("enter x:");
    scanf("%d",&x);
    while(x!=-1)
    {
        new=(node *)malloc(sizeof(node));
        new->data=x;
        new->next=NULL;
        if (first==NULL)
        {
            first=new;
            prev=new;
        }
        else
        {
            prev->next=new;
            prev=new;
        }
        printf("enter x value:");
        scanf("%d",&x);
    }
    return first;
}
void display(node *first)
{
    node *t=first;
    while (t!=NULL)
    {
        printf("%d\n",t->data);
        t=t->next;
}   }
int count(node *first)
{  
    node *t=first;
    int c=0;
    while(t!=NULL)
    {
        c=c+1;
        t=t->next;
    }
    return c;
}
void search(node *first,int dataf)
{
    node *t=first;
    int f=0;
    while (t!=NULL)
    {  
        if (t->data==dataf)
        {
          f+=1;
          break;
        }
        else
        {
            f=0;
        }
    }
    if (f==1)
    {
        printf("dataf found");
    }
    else
    {
        printf("dataf not found");
    }
}
node * insert_begin(node *first,int datains)
{
    node *new;
    new=(node *)malloc(sizeof(node));
    new->data=datains;
    new->next=NULL;
    if (first==NULL)
    {
        first=new;
    }
    else
    {
        new->next=first;
        first=new;
    }
    return first;
}
node * random_insert(node *first,int datains,int datapos)
{  
    int i;
    node *new,*k;
    node *t=first;
    new=(node *)malloc(sizeof(node));
    new->data=datains;
    new->next=NULL;
    if (first==NULL)
    {
        first=new;
    }
    else
    {
       for (i=0;i<datapos-1;i++)
       {
           t=t->next;
       }
       k=t->next;
       t->next=new;
       new->next=k;
    }
    return first;
}
node *last_insert(node *first,int datains)
{  
    int c,i;
    node *new;
    node *t=first;
    new=(node *)malloc(sizeof(node));
    new->data=datains;
    new->next=NULL;
    c=count(first);
    if (first==NULL)
    {
        first=new;
    }
    else
    {
        for (i=0;i<c-1;i++)
        {
            t=t->next;
        }
        t->next=new;
    }
    return first;
}
node *begin_delete(node *first)
{
    first=first->next;
    return first;
}
node *random_delete(node *first,int datapos)
{  
    int i;
    node *t=first;
    node *k,*l;
    for (i=0;i<datapos-1;i++)
    {  
        k=t;
        t=t->next;
        l=t->next;
       
    }
    k->next=l;
    free(t);
    return first;
}
void *sort(node *first)
{
    node *t1,*t2;
    int t;
    for (t1=first;t1->next!=NULL;t1=t1->next)
    {
        for(t2=t1->next;t2!=NULL;t2=t2->next)
        {
            if (t1->data > t2->data)
            {
                t=t1->data;
                t1->data=t2->data;
                t2->data=t;
            }
        }
    }
}
node *reverse(node *first)
{
    node *prev,*pres,*save;
    prev=NULL;
    pres=first;
    while (pres!=NULL)
    {  
        save=pres->next;
        pres->next=prev;
        prev=pres;
        pres=save;
    }
    return prev ;
}
void main()
{  
    node *head=NULL;
    int ch,dataf,datains,datapos,c;
    printf("enter dataf:");
    scanf("%d",&dataf);
    printf("enter datains:");
    scanf("%d",&datains);
    printf("enter datapos:");
    scanf("%d",&datapos);
    while(1)
    {  
      printf("enter ch:");
      scanf("%d",&ch);
      switch(ch)
      {
          case 1:head=create(head);
                 break;
          case 2:display(head);
                 break;
          case 3:c=count(head);
                 printf("no of nodes is %d",c);
                 break;
          case 4:search(head,dataf);
                 break;
          case 5:head=insert_begin(head,datains);
                 break;
          case 6:head=random_insert(head,datains,datapos);
                 break;
          case 7:head=last_insert(head,datains);
                 break;
          case 8:head=begin_delete(head);
                 break;
          case 9:head=random_delete(head,datapos);
                 break;
          case 10:sort(head);
                  break;
          case 11:head=reverse(head);
                  break;
          case 12:exit(0);
         
      }
       
}
}
