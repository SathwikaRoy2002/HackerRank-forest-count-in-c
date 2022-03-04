#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

char land[1000][1000];

void forest(int i, int j, int N)
{
    if(i<0 || j<0 || i>=N || j>=N || land[i][j]!='T')
        return;    
    land[i][j] = 'W';    
    forest(i-1,j,N);//top
    forest(i,j-1,N);//left
    forest(i+1,j,N);//down
    forest(i,j+1,N);//right
}

int main() 
{
    int N,count = 0;
    scanf("%d",&N);    
    for(int i=0; i<N; i++)
        scanf("%s",land[i]);    
    for(int i=0; i<N; i++)
    {
        for(int j=0; j<N; j++)
        {
            if(land[i][j] == 'T')
            {
                count++;
                forest(i,j,N);                
            }
        }
    }
    printf("%d",count);
    return 0;
}
