#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int main() {
    int choice, n, start, length, i, j, indexBlock, block[MAX] = {0}, index[MAX];

    while (1) {
        printf("\n1.Sequential Allocation\n2.Indexed Allocation\n3.Linked Allocation\n4.Exit\nEnter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter starting block and length of file: ");
                scanf("%d %d", &start, &length);
                for (i = start; i < start + length; i++) {
                    if (block[i] == 1) {
                        printf("Block %d already allocated.\n", i);
                        break;
                    }
                }
                if (i == start + length) {
                    for (i = start; i < start + length; i++)
                        block[i] = 1;
                    printf("File allocated from block %d to %d.\n", start, start + length - 1);
                }
                break;

            case 2:
                printf("Enter index block: ");
                scanf("%d", &indexBlock);
                if (block[indexBlock] == 1) {
                    printf("Index block already allocated.\n");
                    break;
                }
                block[indexBlock] = 1;
                printf("Enter number of blocks for the file: ");
                scanf("%d", &n);
                printf("Enter block numbers: ");
                for (i = 0; i < n; i++) {
                    scanf("%d", &index[i]);
                    if (block[index[i]] == 1) {
                        printf("Block %d already allocated.\n", index[i]);
                        i--;
                    } else {
                        block[index[i]] = 1;
                    }
                }
                printf("File allocated at index block %d with blocks: ", indexBlock);
                for (i = 0; i < n; i++)
                    printf("%d ", index[i]);
                printf("\n");
                break;

            case 3:
                printf("Enter starting block and number of blocks: ");
                scanf("%d %d", &start, &length);
                j = start;
                for (i = 0; i < length; i++) {
                    if (block[j] == 0) {
                        block[j] = 1;
                        printf("Block %d allocated.\n", j);
                        j = rand() % MAX;
                    } else {
                        printf("Block %d already allocated, finding next.\n", j);
                        j = rand() % MAX;
                        i--;
                    }
                }
                printf("File allocated using linked allocation.\n");
                break;

            case 4:
                exit(0);

            default:
                printf("Invalid choice.\n");
        }
    }
    return 0;
}
