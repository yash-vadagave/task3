#include <iostream>
using namespace std;

char board[3][3] = {{' ', ' ', ' '}, {' ', ' ', ' '}, {' ', ' ', ' '}};
char Player = 'X';

void displayBoard() 
{
    cout << " " << board[0][0] << " | " << board[0][1] << " | " << board[0][2] << endl;
    cout << "----+----+----" << endl;
    cout << " " << board[1][0] << " | " << board[1][1] << " | " << board[1][2] << endl;
    cout << "----+----+----" << endl;
    cout << " " << board[2][0] << " | " << board[2][1] << " | " << board[2][2] << endl;
}

bool checkWin() 
{
    for (int i = 0; i < 3; i++) 
    {
        if (board[i][0] == Player && board[i][1] == Player && board[i][2] == Player) 
        {
            return true; 
        }
        if (board[0][i] == Player && board[1][i] == Player && board[2][i] == Player) 
        {
            return true; 
        }
    }
    if (board[0][0] == Player && board[1][1] == Player && board[2][2] == Player) 
    {
        return true; 
    }
    if (board[0][2] == Player && board[1][1] == Player && board[2][0] == Player) 
    {
        return true; 
    }
    return false;
}

bool checkDraw() 
{
    for (int i = 0; i < 3; i++) 
    {
        for (int j = 0; j < 3; j++) 
        {
            if (board[i][j] == ' ') 
            {
                return false; 
            }
        }
    }
    return true;
}

int main() 
{
    bool gameWon = false;
    bool gameDraw = false;

    while (!gameWon && !gameDraw) 
    {
        displayBoard();
        int row, col;
        cout << "\nPlayer " << Player << "enter row (0-2) and column (0-2): \n";
        cin >> row >> col;

        if (row >= 0 && row < 3 && col >= 0 && col < 3 && board[row][col] == ' ') 
        {
            board[row][col] = Player;

            if (checkWin()) 
            {
                displayBoard();
                cout << "\nPlayer " << Player << " wins!!\n" << endl;
                gameWon = true;
            } 
            else if (checkDraw()) 
            {
                displayBoard();
                cout << "\nIt's a draw!!\n" << endl;
                gameDraw = true;
            } 
            else 
            {
                Player = (Player == 'X') ? 'O' : 'X';
            }
        } 
        else 
        {
            cout << "\nInvalid move. Try again.\n" << endl;
        }
    }
    return 0;
}
