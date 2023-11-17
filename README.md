# swaping-the-values-in-c
#include <stdio.h>

int main() {
    FILE *file1, *file2;
    char temp[1000]; // Adjust the buffer size as needed

    // Open the first file for reading
    file1 = fopen("file1.txt", "r");
    if (file1 == NULL) {
        perror("Error opening file1.txt");
        return 1;
    }

    // Read the content of file1 into temp
    fread(temp, 1, sizeof(temp), file1);

    // Close the first file
    fclose(file1);

    // Open the second file for reading
    file2 = fopen("file2.txt", "r");
    if (file2 == NULL) {
        perror("Error opening file2.txt");
        return 1;
    }

    // Open the first file for writing
    file1 = fopen("file1.txt", "w");
    if (file1 == NULL) {
        perror("Error opening file1.txt for writing");
        return 1;
    }

    // Read the content of file2 into temp
    fread(temp, 1, sizeof(temp), file2);

    // Close the second file
    fclose(file2);

    // Open the second file for writing
    file2 = fopen("file2.txt", "w");
    if (file2 == NULL) {
        perror("Error opening file2.txt for writing");
        return 1;
    }

    // Write the content of temp to file2
    fwrite(temp, 1, sizeof(temp), file2);

    // Close the files
    fclose(file1);
    fclose(file2);

    printf("Files swapped successfully.\n");

    return 0;
}
