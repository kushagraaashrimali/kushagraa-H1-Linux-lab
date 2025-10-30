#include <stdio.h>

int findLRU(int time[], int n) {
    int i, min = time[0], pos = 0;
    for (i = 1; i < n; ++i) {
        if (time[i] < min) {
            min = time[i];
            pos = i;
        }
    }
    return pos;
}

int findLFU(int freq[], int n) {
    int i, min = freq[0], pos = 0;
    for (i = 1; i < n; ++i) {
        if (freq[i] < min) {
            min = freq[i];
            pos = i;
        }
    }
    return pos;
}

void fifo(int pages[], int n, int frames) {
    int frame[10], i, j, k = 0, flag, count = 0;
    for (i = 0; i < frames; i++) frame[i] = -1;
    for (i = 0; i < n; i++) {
        flag = 0;
        for (j = 0; j < frames; j++) {
            if (frame[j] == pages[i]) {
                flag = 1;
                break;
            }
        }
        if (flag == 0) {
            frame[k] = pages[i];
            k = (k + 1) % frames;
            count++;
        }
    }
    printf("FIFO Page Faults = %d\n", count);
}

void lru(int pages[], int n, int frames) {
    int frame[10], time[10], i, j, pos, count = 0, flag1, flag2, counter = 0;
    for (i = 0; i < frames; ++i) frame[i] = -1;
    for (i = 0; i < n; ++i) {
        flag1 = flag2 = 0;
        for (j = 0; j < frames; ++j) {
            if (frame[j] == pages[i]) {
                counter++;
                time[j] = counter;
                flag1 = flag2 = 1;
                break;
            }
        }
        if (flag1 == 0) {
            for (j = 0; j < frames; ++j) {
                if (frame[j] == -1) {
                    counter++;
                    count++;
                    frame[j] = pages[i];
                    time[j] = counter;
                    flag2 = 1;
                    break;
                }
            }
        }
        if (flag2 == 0) {
            pos = findLRU(time, frames);
            counter++;
            count++;
            frame[pos] = pages[i];
            time[pos] = counter;
        }
    }
    printf("LRU Page Faults = %d\n", count);
}

void lfu(int pages[], int n, int frames) {
    int frame[10], freq[10], i, j, pos, count = 0, flag1, flag2;
    for (i = 0; i < frames; ++i) { frame[i] = -1; freq[i] = 0; }
    for (i = 0; i < n; ++i) {
        flag1 = flag2 = 0;
        for (j = 0; j < frames; ++j) {
            if (frame[j] == pages[i]) {
                freq[j]++;
                flag1 = flag2 = 1;
                break;
            }
        }
        if (flag1 == 0) {
            for (j = 0; j < frames; ++j) {
                if (frame[j] == -1) {
                    frame[j] = pages[i];
                    freq[j] = 1;
                    count++;
                    flag2 = 1;
                    break;
                }
            }
        }
        if (flag2 == 0) {
            pos = findLFU(freq, frames);
            frame[pos] = pages[i];
            freq[pos] = 1;
            count++;
        }
    }
    printf("LFU Page Faults = %d\n", count);
}

int main() {
    int n, frames, pages[30], i;
    printf("Enter number of pages: ");
    scanf("%d", &n);
    printf("Enter reference string: ");
    for (i = 0; i < n; i++) scanf("%d", &pages[i]);
    printf("Enter number of frames: ");
    scanf("%d", &frames);

    fifo(pages, n, frames);
    lru(pages, n, frames);
    lfu(pages, n, frames);
    return 0;
}
