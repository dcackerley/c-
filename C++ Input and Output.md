//Dylan Ackerley COSC 1337 Section 011 MW 5:30pm-8:50pm
//D1696872

#include <iostream>
#include <iomanip> // This library will let us use the std::setprecision function later on, meeting the hundreths of seconds requirement the professor requires.
#include <string> //This is actually included in <iostream> with my compiler "minGW", but I'm going to leave it here in case the professor's compiler is different.
using namespace std;




main() {

    string player1, player2, player3;

    cout << "Please enter a name for runner 1: " << endl;
    getline(cin, player1); // This gets the line of input and assigns it to the string variable of player1
    cout << "Please enter a name for runner 2: " << endl;
    getline(cin, player2); // This gets the line of input and assigns it to the string variable of player2
    cout << "Please enter a name for runner 3: " << endl;
    getline(cin, player3); // This gets the line of input and assigns it to the string variable of player3

    double player1Time, player2Time, player3Time;


    do {
        cout << "Enter a numerical runtime for " << player1 << endl;
        cin >> player1Time; // Will make an infinite loop if anything other than a double is input
    } while (player1Time<=0);

    do {
        cout << "Enter a numerical runtime for " << player2 << endl;
        cin >> player2Time; // Will make an infinite loop if anything other than a double is input
    } while (player2Time<=0);
    do {
        cout << "Enter a numerical runtime for " << player3 << endl;
        cin >> player3Time; // Will make an infinite loop if anything other than a double is input
    } while (player3Time<=0);

    //If player1 wins overall
    if (player1Time < player2Time && player1Time <player3Time) { // If player1 was faster than player 2 and 3, do the following
        if (player2Time < player3Time) { // If player2Time is also better than
            cout << setprecision(2) << fixed;
            cout << "First place goes to " << player1 << " with a runtime of " << player1Time << " seconds" << endl;
            cout << "Second place goes to " << player2 << "with a runtime of " << player2Time << " seconds" << endl;
            cout << "Third place goes to " << player3 << " with a runtime of " << player3Time << " seconds" << endl;
            return(0);
        }
        else (player3Time < player2Time);// Checks if player2 got second, only executes as long as first place is for sure player1, and player3 placed second.
        {
            cout << setprecision(2) << fixed;
            cout << "First place goes to " << player1 << " with a runtime of " << player1Time << " seconds" << endl;
            cout << "Second place goes to " << player3 << " with a runtime of " << player3Time << " seconds" << endl;
            cout << "Third place goes to " << player2 << " with a runtime of " << player2Time << " seconds" << endl;
            return (0);
        }

        }
    //If player2 wins overall
    if (player2Time < player1Time && player2Time <player3Time) {
        if (player1Time < player3Time) {
            cout << setprecision(2) << fixed;
            cout << "First place goes to " << player2 << " with a runtime of " << player2Time << " seconds" << endl;
            cout << "Second place goes to " << player1 << " with a runtime of " << player1Time << " seconds" << endl;
            cout << "Third place goes to " << player3 << " with a runtime of " << player3Time << " seconds" << endl;
            return(0);
        }
        else (player3Time < player1Time);
        {
            cout << setprecision(2) << fixed;
            cout << "First place goes to " << player2 << " with a runtime of " << player2Time << " seconds" << endl;
            cout << "Second place goes to " << player3 << " with a runtime of " << player3Time << " seconds" << endl;
            cout << "Third place goes to " << player1 << " with a runtime of " << player1Time << " seconds" << endl;
            return (0);
        }

    }
    //If player3 wins overall
    if (player3Time < player1Time && player3Time <player2Time) {
        if (player2Time < player1Time) {
            cout << setprecision(2) << fixed;
            cout << "First place goes to " << player3 << " with a runtime of " << player3Time << " seconds" << endl;
            cout << "Second place goes to " << player2 << " with a runtime of " << player2Time << " seconds" << endl;
            cout << "Third place goes to " << player1 << " with a runtime of " << player1Time << " seconds" << endl;
            return(0);
        }
        else (player1Time < player2Time);
        {
            cout << setprecision(2) << fixed;
            cout << "First place goes to " << player3 << " with a runtime of " << player3Time << " seconds" << endl;
            cout << "Second place goes to " << player1 << " with a runtime of " << player1Time << " seconds" << endl;
            cout << "Third place goes to " << player2 << " with a runtime of " << player2Time << " seconds" << endl;
            return (0);
        }

    }
    else
        cout << "Error occurred" << endl;









    return(0);


    return 0;// Verifies if everything above ran fine
}





