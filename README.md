#include<iostream>
#include<cmath>
using namespace std;

void updateState(int& numCoins, int coinsTaken) {
    numCoins -= coinsTaken;
}

bool isWinner(int numCoins) {
    return numCoins < 1;
}

int main() {
    cout << "- To start the game, you should enter the number of coins." << endl;
    cout << "- Players must take a perfect square number of coins like (1, 4, 9, 16, ...)." << endl;
    cout << "- The last player to take coins wins." << endl;
    cout << "- Good luck!" << endl;

    int numCoins;
    cout << "Please enter the maximum number of coins: ";
    cin >> numCoins;

    while (true) {
        int subtractedCoins1;
        cout << "Player 1, please enter the number of coins to subtract: ";
        cin >> subtractedCoins1;

        while (subtractedCoins1 <= 0 || subtractedCoins1 >= numCoins || static_cast<int>(sqrt(subtractedCoins1)) * static_cast<int>(sqrt(subtractedCoins1)) != subtractedCoins1) {
            cout << "Invalid number, please enter a perfect square number: ";
            cin >> subtractedCoins1;
        }

        updateState(numCoins, subtractedCoins1);
        if (isWinner(numCoins)) {
            cout << "Player 1 is the winner!" << endl;
            break;
        }
        else {
            cout << "The remaining coins: " << numCoins << endl;
        }

        int subtractedCoins2;
        cout << "Player 2, please enter the number of coins to subtract: ";
        cin >> subtractedCoins2;

        while (subtractedCoins2 <= 0 || subtractedCoins2 >= numCoins || static_cast<int>(sqrt(subtractedCoins2)) * static_cast<int>(sqrt(subtractedCoins2)) != subtractedCoins2) {
            cout << "Invalid number, please enter a perfect square number: ";
            cin >> subtractedCoins2;
        }

        updateState(numCoins, subtractedCoins2);
        if (isWinner(numCoins)) {
            cout << "Player 2 is the winner!" << endl;
            break;
        }
        else {
            cout << "The remaining coins: " << numCoins << endl;
        }
    }

    return 0;
}
