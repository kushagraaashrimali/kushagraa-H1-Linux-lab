#include <stdio.h>

int findLRU(int time[], int n) {
    int i, minimum = time[0], pos = 0;
    for (i = 1; i < n; ++i) {
        if (time[i] < minimum) {
            minimum = time[i];
            pos = i;
        }
    }
    return pos;
}

int main() {
    int frames[10], pages[30], temp[10], time[10];
    int totalFrames, totalPages, counter = 0, flag1, flag2, faults = 0;
    int i, j, k, pos, choice;

    printf("Enter number of frames: ");
    scanf("%d", &totalFrames);

    printf("Enter number of pages: ");
    scanf("%d", &totalPages);

    printf("Enter the reference string:\n");
    for (i = 0; i < totalPages; ++i)
        scanf("%d", &pages[i]);

    printf("\nSelect Page Replacement Algorithm:\n");
    printf("1. FIFO\n2. LRU\n3. Optimal\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    faults = 0;
    for (i = 0; i < totalFrames; ++i)
        frames[i] = -1;

    switch (choice) {
    case 1: // FIFO
        j = 0;
        for (i = 0; i < totalPages; ++i) {
            flag1 = flag2 = 0;
            for (k = 0; k < totalFrames; ++k) {
                if (frames[k] == pages[i]) {
                    flag1 = flag2 = 1;
                    break;
                }
            }
            if (flag1 == 0) {
                frames[j] = pages[i];
                j = (j + 1) % totalFrames;
                faults++;
            }

            printf("\nPage %d -> ", pages[i]);
            for (k = 0; k < totalFrames; ++k)
                if (frames[k] != -1)
                    printf("%d ", frames[k]);
                else
                    printf("- ");
        }
        break;

    case 2: // LRU
        for (i = 0; i < totalPages; ++i) {
            flag1 = flag2 = 0;
            for (j = 0; j < totalFrames; ++j) {
                if (frames[j] == pages[i]) {
                    counter++;
                    time[j] = counter;
                    flag1 = flag2 = 1;
                    break;
                }
            }
            if (flag1 == 0) {
                for (j = 0; j < totalFrames; ++j) {
                    if (frames[j] == -1) {
                        counter++;
                        faults++;
                        frames[j] = pages[i];
                        time[j] = counter;
                        flag2 = 1;
                        break;
                    }
                }
            }
            if (flag2 == 0) {
                pos = findLRU(time, totalFrames);
                counter++;
                faults++;
                frames[pos] = pages[i];
                time[pos] = counter;
            }

            printf("\nPage %d -> ", pages[i]);
            for (k = 0; k < totalFrames; ++k)
                if (frames[k] != -1)
                    printf("%d ", frames[k]);
                else
                    printf("- ");
        }
        break;

    case 3: // Optimal
        for (i = 0; i < totalPages; ++i) {
            flag1 = flag2 = 0;
            for (j = 0; j < totalFrames; ++j) {
                if (frames[j] == pages[i]) {
                    flag1 = flag2 = 1;
                    break;
                }
            }

            if (flag1 == 0) {
                for (j = 0; j < totalFrames; ++j) {
                    if (frames[j] == -1) {
                        faults++;
                        frames[j] = pages[i];
                        flag2 = 1;
                        break;
                    }
                }
            }

            if (flag2 == 0) {
                for (j = 0; j < totalFrames; ++j)
                    temp[j] = -1;

                for (j = 0; j < totalFrames; ++j) {
                    for (k = i + 1; k < totalPages; ++k) {
                        if (frames[j] == pages[k]) {
                            temp[j] = k;
                            break;
                        }
                    }
                }

                pos = -1;
                int farthest = -1;
                for (j = 0; j < totalFrames; ++j) {
                    if (temp[j] == -1) {
                        pos = j;
                        break;
                    } else if (temp[j] > farthest) {
                        farthest = temp[j];
                        pos = j;
                    }
                }
                frames[pos] = pages[i];
                faults++;
            }

            printf("\nPage %d -> ", pages[i]);
            for (k = 0; k < totalFrames; ++k)
                if (frames[k] != -1)
                    printf("%d ", frames[k]);
                else
                    printf("- ");
        }
        break;

    default:
        printf("Invalid choice!\n");
        return 0;
    }

    printf("\n\nTotal Page Faults = %d\n", faults);
    return 0;
}
