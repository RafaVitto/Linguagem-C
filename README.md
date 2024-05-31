#include <stdio.h>
#include <string.h>

#define MAX_ITENS 100
#define TAM_NOME 50

typedef struct {
    int id;
    char nome[TAM_NOME];
    float unitario;
    int qtde;
    float total_item;
} Item;

int main() {
    int n_itens;
    Item itens[MAX_ITENS];
    int i, j;
    float total_final = 0.0;

    printf("Informe o número de itens que deseja inserir: ");
    scanf("%d", &n_itens);

    for (i = 0; i < n_itens; i++) {
        printf("Informe o código do item %d: ", i + 1);
        scanf("%d", &itens[i].id);

        for (j = 0; j < i; j++) {
            if (itens[i].id == itens[j].id) {
                printf("Código já inserido! Tente novamente.\n");
                i--; 
                break;
            }
        }

        printf("Informe o nome do item %d: ", i + 1);
        scanf("%s", itens[i].nome);

        printf("Informe o valor unitário do item %d: ", i + 1);
        scanf("%f", &itens[i].unitario);

        printf("Informe a quantidade do item %d: ", i + 1);
        scanf("%d", &itens[i].qtde);

        itens[i].total_item = itens[i].unitario * itens[i].qtde;
        total_final += itens[i].total_item;
    }

    printf("\nLista de itens:\n");
    printf("CODIGO    NOME    QTDE    UNIT    TOTAL\n");
    for (i = 0; i < n_itens; i++) {
        printf("%05d %20s %5d %8.2f %8.2f\n", itens[i].id, itens[i].nome, itens[i].qtde, itens[i].unitario, itens[i].total_item);
    }
    printf("TOTAL FINAL %.2f\n", total_final);

    return 0;
}
