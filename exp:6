#include <stdio.h>

int main() {
    int ms, ps, nop, np, rempages, i, j, x, y, pa, offset;
    int s[10], fno[10][20];

    printf("Enter the total memory size (in bytes): ");
    scanf("%d", &ms);
    printf("Enter the page size (in bytes): ");
    scanf("%d", &ps);

    nop = ms / ps;
    printf("Total number of pages available in memory = %d\n", nop);

    printf("Enter number of processes: ");
    scanf("%d", &np);

    rempages = nop;
    for (i = 0; i < np; i++) {
        printf("\nEnter number of pages required for process %d: ", i + 1);
        scanf("%d", &s[i]);
        if (s[i] > rempages)
            printf("Memory is full, cannot allocate for process %d.\n", i + 1);
        else {
            rempages -= s[i];
            printf("Enter page table for process %d (page frame numbers):\n", i + 1);
            for (j = 0; j < s[i]; j++)
                scanf("%d", &fno[i][j]);
        }
    }

    printf("\nEnter process number and page number and offset: ");
    scanf("%d %d %d", &x, &y, &offset);
    if (x > np || y >= s[x - 1])
        printf("Invalid process or page number.\n");
    else {
        pa = fno[x - 1][y] * ps + offset;
        printf("The Physical Address = %d\n", pa);
    }
    return 0;
}
