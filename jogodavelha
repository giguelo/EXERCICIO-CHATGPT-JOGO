#include <stdio.h>

// Função para exibir o tabuleiro
void exibirTabuleiro(char tabuleiro[3][3]) {
    printf("\n  1 2 3\n");
    for (int i = 0; i < 3; i++) {
        printf("%d ", i + 1);
        for (int j = 0; j < 3; j++) {
            printf("%c ", tabuleiro[i][j]);
        }
        printf("\n");
    }
    printf("\n");
}

// Função para verificar o estado do jogo
int verificarVitoria(char tabuleiro[3][3], char jogador) {
    // Verificar linhas e colunas
    for (int i = 0; i < 3; i++) {
        if ((tabuleiro[i][0] == jogador && tabuleiro[i][1] == jogador && tabuleiro[i][2] == jogador) ||
            (tabuleiro[0][i] == jogador && tabuleiro[1][i] == jogador && tabuleiro[2][i] == jogador)) {
            return 1; // Vitória
        }
    }

    // Verificar diagonais
    if ((tabuleiro[0][0] == jogador && tabuleiro[1][1] == jogador && tabuleiro[2][2] == jogador) ||
        (tabuleiro[0][2] == jogador && tabuleiro[1][1] == jogador && tabuleiro[2][0] == jogador)) {
        return 1; // Vitória
    }

    // Verificar empate
    int empate = 1;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (tabuleiro[i][j] == ' ') {
                empate = 0; // Ainda há espaços vazios no tabuleiro
            }
        }
    }
    if (empate) {
        return 0; // Empate
    }

    return -1; // Jogo em andamento
}

// Função para realizar uma jogada
void fazerJogada(char tabuleiro[3][3], int linha, int coluna, char jogador) {
    if (linha >= 0 && linha < 3 && coluna >= 0 && coluna < 3 && tabuleiro[linha][coluna] == ' ') {
        tabuleiro[linha][coluna] = jogador;
    } else {
        printf("Jogada inválida. Tente novamente.\n");
    }
}

int main() {
    char tabuleiro[3][3] = {
        {' ', ' ', ' '},
        {' ', ' ', ' '},
        {' ', ' ', ' '}
    };

    int linha, coluna;
    char jogador = 'X';
    int resultado;

    do {
        exibirTabuleiro(tabuleiro);
        printf("Jogador %c, digite a linha e a coluna (1 a 3) para fazer a sua jogada: ", jogador);
        scanf("%d %d", &linha, &coluna);

        fazerJogada(tabuleiro, linha - 1, coluna - 1, jogador);

        resultado = verificarVitoria(tabuleiro, jogador);

        if (resultado == -1) {
            // Alternar para o próximo jogador
            jogador = (jogador == 'X') ? 'O' : 'X';
        }

    } while (resultado == -1);

    exibirTabuleiro(tabuleiro);

    // Exibir resultado do jogo
    if (resultado == 1) {
        printf("Jogador %c venceu!\n", jogador);
    } else {
        printf("O jogo terminou em empate!\n");
    }

    return 0;
}
