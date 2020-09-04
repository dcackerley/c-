//Dylan Ackerley, d1696872
#include <iomanip>
#include <iostream>
#include <algorithm>
using namespace std;

class Test {
private:
    int size, scores[]; // declerations of both variables we're going to manipulate

public:
    int getScore(int index) { //getter
        return scores[index];
    }

    void setScore(int index, int score) { //setter, doesn't return anything
        scores[index] = score;
    }

    int length() {
        return size;
    }

    void sortScores(){
        sort(scores, scores+size);
    }

    double getAverage() {
        double total = 0;

        for(int x = 0; x < size; ++x) {
            total += scores[x];
        }

        return total/size;
    }

    void displayData() {
        cout << "The scores are: ";
        for(int x = 0; x < size; ++x) {
            cout << scores[x] << " ";
        }
        cout << "\nThe Average of the scores is " << getAverage();
    }
public:
    Test(int a, int arr[]){ //Constructor, allocates size
        size = a;
        for(int x = 0; x < size; ++x) {
            scores[x] = arr[x];
        }
    }

    ~Test() {};
};

int main() {
    int size;
    int *pSize;
    pSize = &size;

    cout << "Enter the number of scores you will be inputting: " << endl;
    cin >> *pSize;
    while (*pSize <=0) {
        cout << "Enter number of scores to record (minimum of 1): " << endl;
        cin  >>*pSize;
    }

    int scores[*pSize];
    int *pScores;
    pScores = scores;

    for(int x = 0; x < *pSize; ++x) {
        cout <<"Enter a score: ";
        cin >>*(pScores + x);
        if (*(pScores + x) < 0) {
            cout <<"Invalid score, reenter a score please: " << endl;
            cin >>*(pScores + x);
        }
    }

    Test a (*pSize, scores);
    a.sortScores(); // instance
    a.displayData(); // instance
}
