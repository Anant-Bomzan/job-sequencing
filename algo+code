/*ALGORITHM
for i = 1 to n do
  Set k = min(dmax, DEADLINE(i))  //where DEADLINE(i) denotes deadline of ith job

  while k >= 1 do
    if timeslot[k] is EMPTY then
      timeslot[k] = job(i)
      break
    endif

    Set k = k - 1

  endwhile

endfor*/

#include <stdio.h>
#define MAX 100

typedef struct Job 
{
    char jb[MAX];
    int deadline;
    int profit;
} Job;

void jobsequencing(Job jobs[], int n);

int minValue(int x, int y) 
{
    if(x < y) 
    return x;
    return y;
}

int main(void) 
{
    int i,j,n;
    Job jobs[MAX];
    printf("Enter the number of jobs: ");
    scanf("%d",&n);
    
    for(i=0;i<n;i++){
        printf("Enter job--> ");
        scanf("%s",&jobs[i].jb);
        printf("Enter the deadline--> ");  
        scanf("%d",&jobs[i].deadline);  
        printf("Enter the profit--> ");  
        scanf("%d",&jobs[i].profit);
    }
  
    Job temp;
    //sort the jobs profit wise in descending order
    for(i=1;i<n;i++) {
        for(j=0; j<n-i;j++) {
            if(jobs[j+1].profit > jobs[j].profit) {
                temp = jobs[j+1];
                jobs[j+1] = jobs[j];
                jobs[j] = temp;
            }
        }
    }

    printf("\nJob\tDeadline\tProfit\n");
    for(i = 0; i < n; i++) {
        printf("%s\t %d\t\t %d\t\n", jobs[i].jb, jobs[i].deadline, jobs[i].profit);
    }
    
    jobsequencing(jobs, n);

    return 0;
}

void jobsequencing(Job jobs[], int n) 
{
    int i,j,k,maxprofit;

    int timeslot[MAX];
    int filledTimeSlot = 0;

    int dmax = 0;
    for(i = 0; i < n; i++) {
        if(jobs[i].deadline > dmax) {
            dmax = jobs[i].deadline;
        }
    }
    for(i = 1; i <= dmax; i++) {
        timeslot[i] = -1;
    }

    printf("\ndmax: %d\n", dmax);

    for(i=1;i<=n;i++) {
        k=minValue(dmax,jobs[i-1].deadline);
        while(k>=1) {
            if(timeslot[k]==-1) {
                timeslot[k]=i-1;
                filledTimeSlot++;
                break;
            }     
            k--;
        }
        if(filledTimeSlot==dmax) {
            break;
        }
    }
    
    printf("\nRequired Jobs: ");
    for(i=1;i<=dmax;i++) {
        printf("%s",jobs[timeslot[i]].jb);

        if(i < dmax) {
            printf(" --> ");
        }
    }
    
    maxprofit=0;
    for(i=1;i<=dmax;i++) {
        maxprofit+=jobs[timeslot[i]].profit;
    }
    printf("\nMax Profit: %d\n", maxprofit);
}


