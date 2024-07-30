#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAX_LEN 100

typedef struct {
    char result[MAX_LEN];
    char arg1[MAX_LEN];
    char op[MAX_LEN];
    char arg2[MAX_LEN];
} TAC;

TAC tac[MAX_LEN];
int tacIndex = 0;
int tempVarIndex = 1;

void generateTAC(char *result, char *arg1, char *op, char *arg2) {
    strcpy(tac[tacIndex].result, result);
    strcpy(tac[tacIndex].arg1, arg1);
    strcpy(tac[tacIndex].op, op);
    strcpy(tac[tacIndex].arg2, arg2);
    tacIndex++;
}

char* newTemp() {
    static char temp[MAX_LEN];
    sprintf(temp, "t%d", tempVarIndex++);
    return temp;
}

void parseExpression(char *expr) {
    char *token;
    char temp1[MAX_LEN], temp2[MAX_LEN], op[MAX_LEN];
    int i = 0;

    token = strtok(expr, " ");
    while (token != NULL) {
        if (isdigit(token[0]) || isalpha(token[0])) {
            if (i == 0) {
                strcpy(temp1, token);
            } else {
                strcpy(temp2, token);
            }
        } else {
            strcpy(op, token);
        }
        i++;
        token = strtok(NULL, " ");
    }

    char *tempResult = newTemp();
    generateTAC(tempResult, temp1, op, temp2);
}

int main() {
    char input[MAX_LEN];
    printf("Enter an arithmetic expression (e.g., a + b): ");
    fgets(input, MAX_LEN, stdin);
    input[strcspn(input, "\n")] = 0; // Remove trailing newline character

    parseExpression(input);

    printf("Three Address Code:\n");
    for (int i = 0; i < tacIndex; i++) {
        printf("%s = %s %s %s\n", tac[i].result, tac[i].arg1, tac[i].op, tac[i].arg2);
    }

    return 0;
}
