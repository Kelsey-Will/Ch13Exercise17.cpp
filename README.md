#include <iostream>
#include <vector>
#include <random>
#include <stdexcept>
using namespace std;

int main() {
    // RNG setup
    random_device rd;
    mt19937 gen(rd());  // Mersenne Twister engine
    uniform_real_distribution<> dist(10.0, 100.0);

    vector<double> numbers;

    try {
        for (int i = 0; i < 25; i++) {
            double num = dist(gen);
            numbers.push_back(num);

            // Exception condition: number in restricted range
            if (num >= 90.0 && num <= 95.0) {
                throw runtime_error("Number in restricted range (90–95).");
            }
        }

        cout << "Generated numbers:\n";
        for (double n : numbers) {
            cout << n << " ";
        }
        cout << endl;

    } catch (const runtime_error& e) {
        cerr << "Exception caught: " << e.what() << endl;
    }

    return 0;
}
