#include <stdio.h>

int main() {
    int nb, np, b[10], p[10], allocation[10], i, j, choice;

    printf("Enter number of blocks: ");
    scanf("%d", &nb);
    printf("Enter size of each block:\n");
    for (i = 0; i < nb; i++) {
        printf("Block %d: ", i + 1);
        scanf("%d", &b[i]);
    }

    printf("Enter number of processes: ");
    scanf("%d", &np);
    printf("Enter size of each process:\n");
    for (i = 0; i < np; i++) {
        printf("Process %d: ", i + 1);
        scanf("%d", &p[i]);
        allocation[i] = -1;
    }

    while (1) {
        printf("\n1. First Fit\n2. Best Fit\n3. Worst Fit\n4. Exit\nEnter your choice: ");
        scanf("%d", &choice);

        int temp[10];
        for (i = 0; i < nb; i++)
            temp[i] = b[i];

        switch (choice) {
            case 1:
                for (i = 0; i < np; i++) {
                    for (j = 0; j < nb; j++) {
                        if (temp[j] >= p[i]) {
                            allocation[i] = j;
                            temp[j] -= p[i];
                            break;
                        }
                    }
                }
                printf("\nFirst Fit Allocation:\n");
                break;

            case 2:
                for (i = 0; i < np; i++) {
                    int best = -1;
                    for (j = 0; j < nb; j++) {
                        if (temp[j] >= p[i]) {
                            if (best == -1 || temp[j] < temp[best])
                                best = j;
                        }
                    }
                    if (best != -1) {
                        allocation[i] = best;
                        temp[best] -= p[i];
                    }
                }
                printf("\nBest Fit Allocation:\n");
                break;

            case 3:
                for (i = 0; i < np; i++) {
                    int worst = -1;
                    for (j = 0; j < nb; j++) {
                        if (temp[j] >= p[i]) {
                            if (worst == -1 || temp[j] > temp[worst])
                                worst = j;
                        }
                    }
                    if (worst != -1) {
                        allocation[i] = worst;
                        temp[worst] -= p[i];
                    }
                }
                printf("\nWorst Fit Allocation:\n");
                break;

            case 4:
                return 0;

            default:
                printf("Invalid choice.\n");
                continue;
        }

        printf("Process\tSize\tBlock\n");
        for (i = 0; i < np; i++) {
            if (allocation[i] != -1)
                printf("%d\t%d\t%d\n", i + 1, p[i], allocation[i] + 1);
            else
                printf("%d\t%d\tNot Allocated\n", i + 1, p[i]);
        }
    }
    return 0;
}
