//Dylan Ackerley

#include <iomanip>
#include <iostream>
#include <algorithm> // The sort algorithm in the STL can sort an array: sort(myarray, myarray + myarraylen);

//Input validation required - nothing less than 1
//We're going to use pointer notation, not array notation


using namespace std;


class Test {
private:
    int *scores; // We'll be using getters and setters to change these. I'll also be able to dynmaically create an instance using a later function.
    int numofScores; // We'll be getting input and sending it to this array
public:
    Test (int a);
    ~Test();
    void sortScores(); // Methods of the class per requirement. Will sort the dynamically created array of scores
    int averageScores(); // will average numofScores with a length variable
    int getScore(int index) const; //gets the current index of a loop later in the program
    int getScore(int index, int score);
    int length() const;

    int *getScores() const;
    //Once we get the dynamically allocated array, we're going to send the length to this.

};

void inputScores(Test &a); //Prototype function that takes a class(instance?)
void showScores (const Test &a);

int main() {
    int scores;
    cout << "Enter the number of scores you will be inputting: ";
    cin >> scores; //This is where we begin taking input to send to the class

    while (scores <=0) {
        cout <<"Enter number of scores to record (minimum of 1): ";
        cin  >>scores;
    }

    Test a(scores);
    inputScores(a); //Function takes .....?
    a.sortScores(); //instance using the getScores() method
    showScores(a);

    cout << "The average of your scores is: " << a.averageScores() << endl;


    return 0;
}
