# rockpaperscissors
My first project

#include <iostream>
#include <cmath>
#include <time.h>
#include <cstdlib>
using namespace std;

const int ROCK = 1;
const int PAPER = 2;
const int SCISSORS = 3;

char ch;
int userValue = 0;

int win = 0;
int draw = 0;
int lose = 0;

int getMachineValue(){
    srand (time(NULL));
    int machineValue = rand() % 3 + 1;
    return machineValue;
}

void determineWinner(int userValue, int machineValue){
    
    if (userValue == ROCK && machineValue == PAPER){
        cout << "Machine wins! Paper wraps rock" << endl;
        lose++;
    }
    else if (userValue == PAPER && machineValue == SCISSORS){
        cout << "Machine wins! Scissors cut paper"
        << endl;
        lose++;
    }
    else if (userValue == SCISSORS && machineValue == ROCK){
        cout << "Machine wins! Rock breaks scissors" << endl;
        lose++;
    }
    else if (userValue == ROCK && machineValue == SCISSORS){
        cout << "You win! Rock breaks scissors" << endl;
        win++;
    }
    else if (userValue == PAPER && machineValue == ROCK){
        cout << "You win! Paper wraps rock" << endl;
        win++;
    }
    else if (userValue == SCISSORS && machineValue == PAPER){
        cout << "You win! Scissors cut paper" << endl;
        win++;
    }
    else if (userValue == SCISSORS && machineValue == SCISSORS){
        cout << "It's a tie!" << endl;
        draw++;
    }
    else if (userValue == ROCK && machineValue == ROCK){
        cout << "It's a tie!" << endl;
        draw++;
    }
    else if (userValue == PAPER && machineValue == PAPER){
        cout << "It's a tie!" << endl;
        draw++;
    }
    else {
        cout << "Please select 1, 2 , or 3: " << endl;
    }
}
void displayValue(int value){
        string result;
        if (value == ROCK){
            result = "Rock";
        }
        else if (value == PAPER){
            result = "PAPER";
        }
        else if (value == SCISSORS){
            result = "Scissors";
        }
        else {
            result = "Wrong value";
        }
        cout << result << endl;
}
    
int main() {

    do{
    cout << '\t' << "Rock Paper Scissors" << endl;
    cout << "Game Menu" << endl;
    cout << "---------" << endl;
    cout << "1. Rock" << endl;
    cout << "2. Paper" << endl;
    cout << "3. Scissors" << endl;
    
    cout << "Enter your value: ";
    cin >> userValue;
    cout << "You selected: ";
    displayValue(userValue);
    
    int machineValue = getMachineValue();
    cout << "The machine selected: ";
    displayValue(machineValue);
    
    determineWinner(userValue, machineValue);
    
    cout << "Wins: " << win << endl;
    cout << "Ties:" << draw << endl;
    cout << "Losses:" << lose << endl;
    cout << "Would you like to play again? Y/N" << endl;
    cin >> ch;
    system("CLS");
    }while(ch == 'Y' || ch == 'y');
    return 0;
}
