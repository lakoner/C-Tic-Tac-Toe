#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <time.h>
#include <string.h>
#include <stdbool.h>

const char player = 'X';
const char computer = 'O';
char board[3][3];


void resetBoard();
void printBoard();
int checkFreeSpaces();
void playerMove();
void computerMove();
char checkWinner();
void printWinner(char);


int main(){
    int res;
    bool response;

    do{
        response = false;
        char winner = ' ';

        resetBoard();

        while(winner == ' ' && checkFreeSpaces() != 0){

            printBoard();

            playerMove();
            winner = checkWinner();
            if(winner != ' ' || checkFreeSpaces() == 0){
                break;
            }

            computerMove();
            winner = checkWinner();
            if(winner != ' ' || checkFreeSpaces() == 0){
                break;
            }
        }

        printBoard();
        printWinner(winner);

        printf("Wanna play again?");
        scanf("%d", &res);

        if(res == 1){
            response = true;
        }
    }while(response);

    return 0;
}

void resetBoard(){

    for(int i = 0; i < 3; i++){

        for(int j = 0; j < 3; j++){
            board[i][j] = ' ';
        }
    }
}

void printBoard(){

    printf("\n %c | %c | %c ", board[0][0], board[0][1], board[0][2]);
    printf("\n---|---|---\n");
    printf(" %c | %c | %c ", board[1][0], board[1][1], board[1][2]);
    printf("\n---|---|---\n");
    printf(" %c | %c | %c ", board[2][0], board[2][1], board[2][2]);
    printf("\n");

}

int checkFreeSpaces(){
    int checkerSpaces = 9;

    for(int i = 0; i < 3; i++){
        for(int j = 0; j < 3; j++){
            if(board[i][j] != ' '){
                checkerSpaces--;
            }
        }
    }
    return checkerSpaces;
}

void playerMove(){

    int row;
    int column;

    do{
        printf("Enter row: ");
        scanf("%d", &row);
        row--;

        printf("Enter column: ");
        scanf("%d", &column);
        column--;

        if(board[row][column] != ' '){
            printf("Invalid move!\n");
        }

        else{
            board[row][column] = player;
            break;
        }

    }while (board[row][column] != ' ');

}

void computerMove(){

    srand(time(0));
    int r, c;
    if(checkFreeSpaces() > 0){
        do{
            r = rand() % 3;
            c = rand() % 3;

        }while(board[r][c] != ' ');

        board[r][c] = computer;

    }

    else{
        printWinner(' ');
    }
}

char checkWinner(){

    for(int i = 0; i < 3; i++){
        if(board[i][0] == board[i][1] && board[i][0] == board[i][2]){
            return board[i][0];
        }
    }

    for(int i = 0; i < 3; i++){
        if(board[0][i] == board[1][i] && board[0][i] == board[2][i]){
            return board[0][i];
        }
    }

    if(board[0][0] == board[1][1] && board[0][0] == board[2][2]){
        return board[0][0];
    }

    if(board[0][2] == board[1][1] && board[0][2] == board[2][0]){
        return board[0][2];
    }

    return ' ';
}

void printWinner(char winner){

    if(winner == player){
        printf("You win!\n");
    }
    else if(winner == computer){
        printf("You lose!\n");
    }
    else{
        printf("It´s a tie!\n");
    }
}
