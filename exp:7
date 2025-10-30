#include <stdio.h>

int main() {
    int n, m, i, j, k;
    int alloc[10][10], max[10][10], avail[10];
    int need[10][10], finish[10], safeSeq[10];
    int count = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);
    printf("Enter number of resource types: ");
    scanf("%d", &m);

    printf("Enter allocation matrix:\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            scanf("%d", &alloc[i][j]);

    printf("Enter maximum matrix:\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            scanf("%d", &max[i][j]);

    printf("Enter available resources:\n");
    for (i = 0; i < m; i++)
        scanf("%d", &avail[i]);

    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++)
            need[i][j] = max[i][j] - alloc[i][j];
        finish[i] = 0;
    }

    while (count < n) {
        int found = 0;
        for (i = 0; i < n; i++) {
            if (finish[i] == 0) {
                int canRun = 1;
                for (j = 0; j < m; j++) {
                    if (need[i][j] > avail[j]) {
                        canRun = 0;
                        break;
                    }
                }
                if (canRun) {
                    for (k = 0; k < m; k++)
                        avail[k] += alloc[i][k];
                    safeSeq[count++] = i;
                    finish[i] = 1;
                    found = 1;
                }
            }
        }
        if (!found) {
            printf("System is in Deadlock!\n");
            return 0;
        }
    }

    printf("\nSystem is in Safe State.\nSafe Sequence: ");
    for (i = 0; i < n; i++)
        printf("P%d ", safeSeq[i]);
    printf("\n");

    return 0;
}
