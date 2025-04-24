# Matrix
#include <stdio.h>

// Function to safely read an integer input
int readInt() {
    int value;
    while (scanf("%d", &value) != 1) {
        printf("Invalid input. Please enter a valid integer: ");
        while(getchar() != '\n');  // Clear the input buffer
    }
    return value;
}

// Function to input matrix elements
void inputMatrix(int matrix[][100], int size, char matrixName) {
    printf("Enter elements of Matrix %c (%dx%d):\n", matrixName, size, size);
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < size; j++) {
            printf("%c[%d][%d]: ", matrixName, i, j);
            matrix[i][j] = readInt();
        }
    }
}

// Function to display a matrix
void displayMatrix(int matrix[][100], int size, char matrixName) {
    printf("\nMatrix %c:\n", matrixName);
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < size; j++)
            printf("%4d", matrix[i][j]);
        printf("\n");
    }
}

// Main function
int main() {
    int size;

    // Ask the user for matrix size
    printf("Enter the size of the matrix: ");
    size = readInt();

    // Dynamic matrix allocation based on user input size
    int A[size][size], B[size][size];
    int sum[size][size], diff[size][size], product[size][size];

    // Input matrices A and B
    inputMatrix(A, size, 'A');
    inputMatrix(B, size, 'B');

    // Matrix Addition
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < size; j++) {
            sum[i][j] = A[i][j] + B[i][j];
        }
    }

    // Matrix Subtraction
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < size; j++) {
            diff[i][j] = A[i][j] - B[i][j];
        }
    }

    // Matrix Multiplication
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < size; j++) {
            product[i][j] = 0;
            for (int k = 0; k < size; k++) {
                product[i][j] += A[i][k] * B[k][j];
            }
        }
    }

    // Display results
    displayMatrix(sum, size, 'S');
    displayMatrix(diff, size, 'D');
    displayMatrix(product, size, 'P');

    return 0;
}
