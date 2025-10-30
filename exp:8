#include <stdio.h>
#include <stdlib.h>

void fcfs(int req[], int n, int head) {
    int i, seek = 0;
    printf("\nFCFS Order: %d", head);
    for (i = 0; i < n; i++) {
        seek += abs(req[i] - head);
        head = req[i];
        printf(" -> %d", head);
    }
    printf("\nTotal Seek Time = %d\n", seek);
    printf("Average Seek Time = %.2f\n", (float)seek / n);
}

void scan(int req[], int n, int head, int disk_size) {
    int i, j, seek = 0, dir, temp;
    int left[50], right[50], l = 0, r = 0;
    printf("Enter direction (1 for high, 0 for low): ");
    scanf("%d", &dir);

    if (dir == 1) right[r++] = disk_size - 1;
    else left[l++] = 0;

    for (i = 0; i < n; i++) {
        if (req[i] < head)
            left[l++] = req[i];
        if (req[i] > head)
            right[r++] = req[i];
    }

    for (i = 0; i < l - 1; i++)
        for (j = i + 1; j < l; j++)
            if (left[i] < left[j]) { temp = left[i]; left[i] = left[j]; left[j] = temp; }

    for (i = 0; i < r - 1; i++)
        for (j = i + 1; j < r; j++)
            if (right[i] > right[j]) { temp = right[i]; right[i] = right[j]; right[j] = temp; }

    printf("\nSCAN Order: %d", head);
    if (dir == 1) {
        for (i = 0; i < r; i++) {
            seek += abs(right[i] - head);
            head = right[i];
            printf(" -> %d", head);
        }
        for (i = 0; i < l; i++) {
            seek += abs(head - left[i]);
            head = left[i];
            printf(" -> %d", head);
        }
    } else {
        for (i = 0; i < l; i++) {
            seek += abs(head - left[i]);
            head = left[i];
            printf(" -> %d", head);
        }
        for (i = 0; i < r; i++) {
            seek += abs(right[i] - head);
            head = right[i];
            printf(" -> %d", head);
        }
    }
    printf("\nTotal Seek Time = %d\n", seek);
    printf("Average Seek Time = %.2f\n", (float)seek / n);
}

void cscan(int req[], int n, int head, int disk_size) {
    int i, j, seek = 0, temp;
    int left[50], right[50], l = 0, r = 0;

    right[r++] = disk_size - 1;
    left[l++] = 0;

    for (i = 0; i < n; i++) {
        if (req[i] < head)
            left[l++] = req[i];
        if (req[i] > head)
            right[r++] = req[i];
    }

    for (i = 0; i < l - 1; i++)
        for (j = i + 1; j < l; j++)
            if (left[i] > left[j]) { temp = left[i]; left[i] = left[j]; left[j] = temp; }

    for (i = 0; i < r - 1; i++)
        for (j = i + 1; j < r; j++)
            if (right[i] > right[j]) { temp = right[i]; right[i] = right[j]; right[j] = temp; }

    printf("\nC-SCAN Order: %d", head);
    for (i = 0; i < r; i++) {
        seek += abs(right[i] - head);
        head = right[i];
        printf(" -> %d", head);
    }

    seek += abs(disk_size - 1 - 0);
    head = 0;

    for (i = 0; i < l; i++) {
        seek += abs(left[i] - head);
        head = left[i];
        printf(" -> %d", head);
    }

    printf("\nTotal Seek Time = %d\n", seek);
    printf("Average Seek Time = %.2f\n", (float)seek / n);
}

int main() {
    int n, req[50], head, disk_size, i;

    printf("Enter number of requests: ");
    scanf("%d", &n);
    printf("Enter request sequence: ");
    for (i = 0; i < n; i++)
        scanf("%d", &req[i]);
    printf("Enter initial head position: ");
    scanf("%d", &head);
    printf("Enter total disk size: ");
    scanf("%d", &disk_size);

    fcfs(req, n, head);
    scan(req, n, head, disk_size);
    cscan(req, n, head, disk_size);

    return 0;
}
