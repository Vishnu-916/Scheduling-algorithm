# Scheduling-algorithm First Come First Serve
#include <stdio.h>
int main()
{
    int pro,i;
    int bst[10],wt[10],tat[10],exu[10];
    float awt=0,atat=0;
    printf("\nFCFS PROCESS SCHEDULING ALGORITHM\n");
    printf("\nENTER NUMBER OF PROCESSES: ");
    scanf("%d",&pro);
    printf("\nENTER BURST TIME FOR EACH PROCESS:\n");
    for(i=0;i<pro;i++)
    {
        scanf("%d",&bst[i]);
    }
    exu[0]=0;
    for(i=1;i<pro;i++)
    {
        exu[i]=exu[i-1]+bst[i-1];
    }
    for(i=0;i<pro;i++)
    {
        wt[i]=exu[i];
        tat[i]=wt[i]+bst[i];
    }
    for(i=0;i<pro;i++)
    {
        awt+=wt[i];
        atat+=tat[i];
    }
    printf("\nPROCESS | BURST TIME | WAITING TIME | TURNAROUND TIME\n");
    for(i=0;i<pro;i++)
    {
        printf("P%d\t | %d\t\t | %d\t\t | %d\n",i+1,bst[i],wt[i],tat[i]);
    }
    printf("\nAVERAGE WAITING TIME = %.2f\n", awt/pro);
    printf("AVERAGE TURNAROUND TIME = %.2f\n", atat/pro);
    return 0;
}
