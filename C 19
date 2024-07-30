#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAX_LEN 100

typedef struct {
    char op[MAX_LEN];
    char arg1[MAX_LEN];
    char arg2[MAX_LEN];
    char result[MAX_LEN];
} Instruction;

Instruction instructions[MAX_LEN];
int instrIndex = 0;
int tempVarIndex = 1;

void generateInstruction(char *op, char *arg1, char *arg2, char *result) {
    strcpy(instructions[instrIndex].op, op);
    strcpy(instructions[instrIndex].arg1, arg1);
    strcpy(instructions[instrIndex].arg2, arg2);
    strcpy(instructions[instrIndex].result, result);
    instrIndex++;
}

char* newTemp() {
    static char temp[MAX_LEN];
    sprintf(temp, "t%d", tempVarIndex++);
    return temp;
}

void parsePostfixExpression(char *expr) {
    char *token;
    char stack[MAX_LEN][MAX_LEN];
    int stackIndex = 0;

    token = strtok(expr, " ");
    while (token != NULL) {
        if (isdigit(token[0]) || isalpha(token[0])) {
            strcpy(stack[stackIndex++], token);
        } else {
            char arg2[MAX_LEN], arg1[MAX_LEN], result[MAX_LEN];
            strcpy(arg2, stack[--stackIndex]);
            strcpy(arg1, stack[--stackIndex]);
            strcpy(result, newTemp());
            generateInstruction(token, arg1, arg2, result);
            strcpy(stack[stackIndex++], result);
        }
        token = strtok(NULL, " ");
    }
}

int main() {
    char input[MAX_LEN];
    printf("Enter a postfix expression (e.g., 'a b +'): ");
    fgets(input, MAX_LEN, stdin);
    input[strcspn(input, "\n")] = 0; // Remove trailing newline character

    parsePostfixExpression(input);

    printf("Generated Instructions:\n");
    for (int i = 0; i < instrIndex; i++) {
        printf("%s = %s %s %s\n", instructions[i].result, instructions[i].arg1, instructions[i].op, instructions[i].arg2);
    }

    return 0;
}
