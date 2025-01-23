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

2. Here’s a C program that can dynamically increase or decrease both:
---------------------------------------------------------------------------
a>Number of subarrays (rows).
b>Number of elements in each subarray (columns).

#include <stdio.h>
#include <stdlib.h>

void resize2DArray(int ***arr, int *rows, int *cols, int newRows, int newCols) {<br><br>
    *arr = realloc(*arr, newRows * sizeof(int *)); // Resize rows<br><br>
    for (int i = 0; i < newRows; i++) {<br><br>
        (*arr)[i] = realloc(i < *rows ? (*arr)[i] : NULL, newCols * sizeof(int)); // Resize or add new rows<br><br>
        for (int j = (i >= *rows ? 0 : *cols); j < newCols; j++) (*arr)[i][j] = 0; // Initialize new elements<br><br>
    }<br><br>
    *rows = newRows;<br><br>
    *cols = newCols;<br><br>
}<br><br>

int main() {<br><br>
    int **arr = NULL, rows = 2, cols = 3;<br><br>
    arr = malloc(rows * sizeof(int *));<br><br>
    for (int i = 0; i < rows; i++) {<br><br>
        arr[i] = malloc(cols * sizeof(int));<br><br>
        for (int j = 0; j < cols; j++) arr[i][j] = i * cols + j + 1; // Initialize<br><br>
    }<br><br>

    printf("Original Array:\n");<br><br>
    for (int i = 0; i < rows; i++, printf("\n"))<br><br>
        for (int j = 0; j < cols; j++) printf("%d ", arr[i][j]);<br><br>

    resize2DArray(&arr, &rows, &cols, 3, 4); // Resize<br><br>

    printf("\nResized Array:\n");<br><br>
    for (int i = 0; i < rows; i++, printf("\n"))<br><br>
        for (int j = 0; j < cols; j++) printf("%d ", arr[i][j]);<br><br>

    for (int i = 0; i < rows; i++) free(arr[i]);<br><br>
    free(arr);<br><br>
    return 0;<br><br>
}<br><br>
