#include <stdio.h>

struct process {
    int pid, arrival, burst, priority, waiting, turnaround, remaining;
};

void calculateAverage(struct process p[], int n) {
    float totalWT = 0, totalTAT = 0;
    for(int i=0; i<n; i++) {
        totalWT += p[i].waiting;
        totalTAT += p[i].turnaround;
    }
    printf("\nAverage Waiting Time = %.2f", totalWT/n);
    printf("\nAverage Turnaround Time = %.2f\n", totalTAT/n);
}

void fcfs(struct process p[], int n) {
    printf("\nFCFS Scheduling\n");
    int time = 0;
    for(int i=0; i<n; i++) {
        if(time < p[i].arrival)
            time = p[i].arrival;
        p[i].waiting = time - p[i].arrival;
        time += p[i].burst;
        p[i].turnaround = p[i].waiting + p[i].burst;
    }
    printf("PID\tAT\tBT\tWT\tTAT\n");
    for(int i=0; i<n; i++)
        printf("%d\t%d\t%d\t%d\t%d\n", p[i].pid, p[i].arrival, p[i].burst, p[i].waiting, p[i].turnaround);
    calculateAverage(p, n);
}

void sjf(struct process p[], int n) {
    printf("\nSJF Scheduling\n");
    int completed = 0, time = 0, visited[100] = {0};
    while(completed < n) {
        int idx = -1, minBT = 9999;
        for(int i=0; i<n; i++) {
            if(p[i].arrival <= time && !visited[i] && p[i].burst < minBT) {
                minBT = p[i].burst;
                idx = i;
            }
        }
        if(idx == -1) { time++; continue; }
        visited[idx] = 1;
        p[idx].waiting = time - p[idx].arrival;
        time += p[idx].burst;
        p[idx].turnaround = p[idx].waiting + p[idx].burst;
        completed++;
    }
    printf("PID\tAT\tBT\tWT\tTAT\n");
    for(int i=0; i<n; i++)
        printf("%d\t%d\t%d\t%d\t%d\n", p[i].pid, p[i].arrival, p[i].burst, p[i].waiting, p[i].turnaround);
    calculateAverage(p, n);
}

void priorityScheduling(struct process p[], int n) {
    printf("\nPriority Scheduling\n");
    int completed = 0, time = 0, visited[100] = {0};
    while(completed < n) {
        int idx = -1, minP = 9999;
        for(int i=0; i<n; i++) {
            if(p[i].arrival <= time && !visited[i] && p[i].priority < minP) {
                minP = p[i].priority;
                idx = i;
            }
        }
        if(idx == -1) { time++; continue; }
        visited[idx] = 1;
        p[idx].waiting = time - p[idx].arrival;
        time += p[idx].burst;
        p[idx].turnaround = p[idx].waiting + p[idx].burst;
        completed++;
    }
    printf("PID\tAT\tBT\tPR\tWT\tTAT\n");
    for(int i=0; i<n; i++)
        printf("%d\t%d\t%d\t%d\t%d\t%d\n", p[i].pid, p[i].arrival, p[i].burst, p[i].priority, p[i].waiting, p[i].turnaround);
    calculateAverage(p, n);
}

void roundRobin(struct process p[], int n, int q) {
    printf("\nRound Robin Scheduling\n");
    int time = 0, completed = 0;
    for(int i=0; i<n; i++)
        p[i].remaining = p[i].burst;
    while(completed < n) {
        int done = 1;
        for(int i=0; i<n; i++) {
            if(p[i].remaining > 0) {
                done = 0;
                if(p[i].remaining > q) {
                    time += q;
                    p[i].remaining -= q;
                } else {
                    time += p[i].remaining;
                    p[i].waiting = time - p[i].burst - p[i].arrival;
                    p[i].remaining = 0;
                    p[i].turnaround = p[i].waiting + p[i].burst;
                    completed++;
                }
            }
        }
        if(done) break;
    }
    printf("PID\tAT\tBT\tWT\tTAT\n");
    for(int i=0; i<n; i++)
        printf("%d\t%d\t%d\t%d\t%d\n", p[i].pid, p[i].arrival, p[i].burst, p[i].waiting, p[i].turnaround);
    calculateAverage(p, n);
}

int main() {
    int n, q;
    struct process p[100];
    printf("Enter number of processes: ");
    scanf("%d", &n);
    for(int i=0; i<n; i++) {
        p[i].pid = i+1;
        printf("P%d Arrival Burst Priority: ", i+1);
        scanf("%d%d%d", &p[i].arrival, &p[i].burst, &p[i].priority);
    }
    fcfs(p, n);
    sjf(p, n);
    priorityScheduling(p, n);
    printf("\nEnter Quantum: ");
    scanf("%d", &q);
    roundRobin(p, n, q);
    return 0;
}
