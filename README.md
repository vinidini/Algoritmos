# Jogo de adivinhação
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void jogarAdivinhacao() {
    int numeroGerado, palpite, tentativas, maxTentativas = 5, continuar = 1;
    int pontos = 0;

    srand(time(NULL)); // Inicializa o gerador de números aleatórios

    while (continuar) {
        numeroGerado = rand() % 100 + 1; // Número aleatório entre 1 e 100
        tentativas = 0;
        printf("\nUm número entre 1 e 100 foi gerado. Tente adivinhar!\n");

        while (tentativas < maxTentativas) {
            printf("Digite seu palpite: ");
            scanf("%d", &palpite);
            tentativas++;

            if (palpite == numeroGerado) {
                printf("Parabéns! Você acertou o número %d em %d tentativa(s)!\n", numeroGerado, tentativas);
                pontos += 10; // Incrementa pontos
                break;
            } else if (palpite < numeroGerado) {
                printf("Tente um número maior.\n");
            } else {
                printf("Tente um número menor.\n");
            }
        }

        if (tentativas == maxTentativas && palpite != numeroGerado) {
            printf("Você não conseguiu adivinhar o número %d.\n", numeroGerado);
        }

        printf("Deseja jogar novamente? Digite 1 para SIM ou 0 para NÃO: ");
        scanf("%d", &continuar);
    }

    printf("Jogo encerrado. Sua pontuação final foi: %d\n", pontos);
}

int main() {
    int escolha;

    printf("Bem-vindo ao Jogo de Adivinhação!\n");
    printf("1. Jogar\n");
    printf("2. Sair\n");
    printf("Escolha uma opção: ");
    scanf("%d", &escolha);

    if (escolha == 1) {
        jogarAdivinhacao();
    } else {
        printf("Obrigado por jogar!\n");
    }

    return 0;
}
