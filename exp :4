#include <stdio.h>

int main() {
    int choice, ms, bs, nob, ef, n, mp[10], tif, i, p=0;

    while (1) {
        printf("\n1. MFT\n2. MVT\n3. Exit\nEnter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter total memory available (in Bytes): ");
                scanf("%d", &ms);
                printf("Enter block size (in Bytes): ");
                scanf("%d", &bs);
                nob = ms / bs;
                ef = ms - nob * bs;
                printf("Enter number of processes: ");
                scanf("%d", &n);
                if (n > nob)
                    printf("Memory full, only %d processes can be accommodated.\n", nob);
                tif = 0;
                for (i = 0; i < n && i < nob; i++) {
                    printf("Enter memory required for process %d (in Bytes): ", i + 1);
                    scanf("%d", &mp[i]);
                    if (mp[i] > bs)
                        printf("Process %d cannot be allocated, exceeds block size.\n", i + 1);
                    else {
                        printf("Process %d allocated in block %d.\n", i + 1, i + 1);
                        tif += bs - mp[i];
                    }
                }
                printf("Total Internal Fragmentation = %d\n", tif);
                printf("Total External Fragmentation = %d\n", ef);
                break;

            case 2:
                printf("Enter total memory available (in Bytes): ");
                scanf("%d", &ms);
                printf("Enter number of processes: ");
                scanf("%d", &n);
                int total = 0;
                for (i = 0; i < n; i++) {
                    printf("Enter memory required for process %d (in Bytes): ", i + 1);
                    scanf("%d", &mp[i]);
                    total += mp[i];
                }
                if (total > ms)
                    printf("Memory is not sufficient, remaining memory = %d\n", ms - (total - mp[i-1]));
                else {
                    printf("All processes allocated successfully.\n");
                    printf("Total Memory Allocated = %d\n", total);
                    printf("External Fragmentation = %d\n", ms - total);
                }
                break;

            case 3:
                return 0;

            default:
                printf("Invalid choice.\n");
        }
    }
}
