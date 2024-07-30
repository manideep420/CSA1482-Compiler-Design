#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

void analyzeFile(FILE *file, int *charCount, int *wordCount, int *lineCount) {
    char ch;
    int inWord = 0;

    *charCount = 0;
    *wordCount = 0;
    *lineCount = 0;

    while ((ch = fgetc(file)) != EOF) {
        (*charCount)++;

        if (ch == '\n') {
            (*lineCount)++;
        }

        if (isspace(ch)) {
            inWord = 0;
        } else if (inWord == 0) {
            inWord = 1;
            (*wordCount)++;
        }
    }

    // Increment line count for the last line if the file does not end with a newline
    if (*charCount > 0 && ch != '\n') {
        (*lineCount)++;
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

    int charCount, wordCount, lineCount;
    analyzeFile(file, &charCount, &wordCount, &lineCount);

    fclose(file);

    printf("Number of characters: %d\n", charCount);
    printf("Number of words: %d\n", wordCount);
    printf("Number of lines: %d\n", lineCount);

    return 0;
}
