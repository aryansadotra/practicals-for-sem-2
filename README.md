# practicals-for-sem-2
here are the practicals that we can use

1. Write a c program to increase or decrease the existing size of an 1D array
----------------------------------------------------------------------------
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *raju, size, newSize;

    // Initial array allocation
    printf("Enter initial size of hair of the raju: ");
    scanf("%d", &size);
    raju = (int *)malloc(size * sizeof(int));
    if (raju == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }

    // Initialize array
    for (int i = 0; i < size; i++) {
        raju[i] = i + 1;
    }

    // Display initial array
    printf("Initial raju: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", raju[i]);
    }
    printf("\n");

    // Resize array
    printf("Enter new size of hair of the raju: ");
    scanf("%d", &newSize);
    raju = (int *)realloc(raju, newSize * sizeof(int));
    if (raju == NULL) {
        printf("Memory reallocation failed!\n");
        return 1;
    }

    // Initialize new elements if size increased
    if (newSize > size) {
        for (int i = size; i < newSize; i++) {
            raju[i] = 0; // Initialize new elements to 0
        }
    }

    // Display resized array
    printf("Resized raju: ");
    for (int i = 0; i < newSize; i++) {
        printf("%d ", raju[i]);
    }
    printf("\n");

    free(raju); // Free memory
    return 0;
}

