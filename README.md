# DAA-Quiz-2
DAA 2nd Quiz Project (Group 12)

Index |
--- | 
[Problem Abstraction](#problemabstraction) |
[Design Analysis Algorithms](#daa) |
[Source Code](#filecpp) |

### <a name="problemabstraction" ></a>Problem Abstraction

---

  Based on Dijkstra’s History: What is the shortest way to travel from Rotterdam to Groningen, 
in general: from given city to given city. It is the algorithm for the shortest path, which I 
designed in about twenty minutes. One morning I was shopping in Amsterdam with my young fiancée, 
and tired, we sat down on the café terrace to drink a cup of coffee and I was just thinking about 
whether I could do this, and I then designed the algorithm for the shortest path. As I said, it was 
a twenty-minute invention. In fact, it was published in ’59, three years late. The publication is 
still readable; it is, in fact, quite nice. One of the reasons that it is so nice was that I designed 
it without pencil and paper. I learned later that one of the advantages of designing without pencil 
and paper is that you are almost forced to avoid all avoidable complexities. Eventually that algorithm 
became, to my great amazement, one of the cornerstones of my fame. — Edsger Dijkstra, in an interview
with Philip L. Frana, Communications of the ACM, 2001.

---

### <a name="daa" ></a>Design Analysis Algorithms

---

We made this program to find the shortest distance between two cities (vertices). We are using Dijkstra’s Algorithm to solve this. At first you will be asked to write down the distance(edge) between two cities as asked by the program and after that you will be asked which one will be the start city(vertex) and which one will be your destination, and then it will compute the shortest distance it could find, and also the path.

---

### <a name="filecpp" ></a>Source Code

``` cpp
/* Dijkstra's Algorithm in C */
#include<stdio.h>
#include<conio.h>
#include<process.h>
#include<string.h>
#include<math.h>
#define IN 99
#define N 5 //change this number the same as the number of the city/vertices you have
int dijkstra(int cost[][N], int source, int target);

int dijsktra(int cost[][N],int source,int target)
{
    int dist[N],prev[N],selected[N]={0},i,m,min,start,d,j;
    char path[N];
    for(i=1;i<= N;i++)
    {
        dist[i] = IN;
        prev[i] = -1;
    }
    start = source;
    selected[start]=1;
    dist[start] = 0;
    while(selected[target] ==0)
    {
        min = IN;
        m = 0;
        for(i=1;i<= N;i++)
        {
            d = dist[start] +cost[start][i];
            if(d< dist[i]&&selected[i]==0)
            {
                dist[i] = d;
                prev[i] = start;
            }
            if(min>dist[i] && selected[i]==0)
            {
                min = dist[i];
                m = i;
            }
        }
        start = m;
        selected[start] = 1;
    }
    start = target;
    j = 0;
    while(start != -1)
    {
        path[j++] = start+64;
        start = prev[start];
    }
    path[j]='\0';
    strrev(path);
    printf("%s", path);
    return dist[target];
}

int main()
{
    int cost[N][N],i,j,w,ch,co;
    int source, target,x,y;
    printf("\t The Shortest Path Algorithm ( DIJKSTRA'S ALGORITHM in C \n\n");
    for(i=1;i<= N;i++)
    for(j=1;j<= N;j++)
    cost[i][j] = IN;
    for(x=1;x<= N;x++)
    {
        for(y=x+1;y<= N;y++)
        {
            printf("Enter the weight of the path between nodes %d and %d: ",x,y);
            scanf("%d",&w);
            cost [x][y] = cost[y][x] = w;
        }
        printf("\n");
    }
    printf("\nEnter the source:");
    scanf("%d", &source);
    printf("\nEnter the target:");
    scanf("%d", &target);
    co = dijsktra(cost,source,target);
    printf("\nThe Shortest Path: %d",co);
}
```

__How To Use__

Before you run the program you have to set how many cities (vertices) you have on line 8, make sure to match it to the amount.  After you run the program, you will be asked to state the distance between each city (vertices) that stated by the program and after that, state the source and target.

__Input and Output__

![Input_and_Output](https://github.com/rimasirfansyah11/DAA-Quiz-2/blob/master/input%20and%20output.PNG)

__Analysis__

Based on the picture in Input and Output, we can declare that there are 5 cities (vertices). Each resemble a letter; A, B, C, D, and E. And also there are the declarations of each distance. After being asked which one is the source and target, it will calculate the shortest distance it could find and then state the nodes we should go through to achieve that goal.

__Note__

While grade was based on contribution on github, we didn’t use it really much since we done this project while gathering together and found that we didn’t really need to use that to pull or push the project, so we do hope that our grades it will divide fairly.

