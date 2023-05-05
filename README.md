# un-directedgraph_adj





[4:58 pm, 05/05/2023] Akshay Pawar: #include<stdio.h>
#include<stdlib.h>
#define SIZE 10
#define NEWNODE (struct node *)malloc(sizeof(struct node))
struct node
{
int vertex;
struct node *next;
};
struct node *AL[SIZE];
int nov;
int noe;
void init(struct node *L[])
{
int i;
for( i=0; i<SIZE; i++)
{
L[i] = NULL;
}
}
void add_in_list(struct node *L[],int i, int v)
{
struct node *t, *l;
t = NEWNODE;
t->vertex = v;
t->next =NULL;
[4:59 pm, 05/05/2023] Akshay Pawar: if(L[i]==NULL)
{
L[i] = t;
}
else
{
t->next = L[i];
L[i] = t;
}
}
void free_list(struct node *L[])
{
int i;
struct node *s, *t;
for( i=0; i<nov; i++)
{
s=L[i];
while(s != NULL )
{
t = s;
s = s->next;
free(t);
}
L[i]=NULL;
}
}
void accept()
{
int i,j,k;
printf("How many Vertices : ");
scanf("%d", &nov);
printf("How many Edges : ");
scanf("%d", &noe);
[4:59 pm, 05/05/2023] Akshay Pawar: for(k=1; k<=noe; k++)
{
printf("Enter Edge (Vi,Vj) : ");
scanf("%d %d", &i,&j);
add_in_list(AL,i,j);
add_in_list(AL,j,i);
}
}
void display(struct node *L[])
{
int i;
struct node *t;
printf("\nAdjacency List\n");
printf("-----------------------\n");
for( i=0; i < nov; i++ )
{
printf("V%d -> ", i);
for( t=L[i]; t!=NULL; t = t->next)
{
printf(" [%d] -> ", t->vertex);
}
printf(" NULL \n");
}
}
void display_degree(struct node *L[])
{
int i,total;
struct node *t;
printf("\nTotal Degree of each Vertex\n");
printf("-------------------------------\n
[4:59 pm, 05/05/2023] Akshay Pawar: for( i=0; i<nov; i++)
{
total = 0;
for( t = L[i]; t!= NULL; t=t->next)
{
total++;
} 
printf("Total Degree of V%d : %d \n", i, total);
}
}
int main()
{
init(AL);
accept();
display(AL);
display_degree(AL);
free_list(AL);
return 0;
}
OUTPUT
sachin@tca2009:$ gcc undirected_adjacency_list.c 
sachin@tca2009:$ ./a.out
How many Vertices : 4
How many Edges : 5
Enter Edge (Vi,Vj) : 0 1
Enter Edge (Vi,Vj) : 1 3
Enter Edge (Vi,Vj) : 2 3
Enter Edge (Vi,Vj) : 0 2
Enter Edge (Vi,Vj) : 0 3
