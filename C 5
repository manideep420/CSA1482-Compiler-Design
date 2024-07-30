#include <stdio.h>
#include <stdlib.h>

// Function to count whitespaces and newlines
void count_whitespaces_and_newlines(FILE *file, int *whitespace_count, int *newline_count) {
    char ch;
    *whitespace_count = 0;
    *newline_count = 0;

    while ((ch = fgetc(file)) != EOF) {
        if (ch == ' ' || ch == '\t') {
            (*whitespace_count)++;
        } else if (ch == '\n') {
            (*newline_count)++;
        }
    }
}

int main(int argc, char *argv[]) {
    if (argc != 2) {
        printf("Usage: %s <filename>\n", argv[0]);
        return 1;
    }

    FILE *file = fopen(argv[1], "r");
    if (file == NULL) {
        perror("Error opening file");
        return 1;
    }

    int whitespace_count, newline_count;
    count_whitespaces_and_newlines(file, &whitespace_count, &newline_count);

    fclose(file);

    printf("Number of whitespace characters: %d\n", whitespace_count);
    printf("Number of newline characters: %d\n", newline_count);

    return 0;
}
