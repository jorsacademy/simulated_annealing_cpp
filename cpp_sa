#include <iostream>
#include <cmath>
#include <cstdlib>
#include <ctime>

// Function to minimize
double objectiveFunction(double x) {
    return x * x;
}

// Simulated annealing algorithm
double simulatedAnnealing(double start_temp, double end_temp, double cooling_rate, double start_x) {
    double temp = start_temp;
    double x = start_x;
    double best_x = x;
    double best_f = objectiveFunction(x);

    srand(time(NULL)); // Seed for random number generation

    while (temp > end_temp) {
        // Generate a new candidate solution nearby
        double new_x = x + ((rand() % 2000 - 1000) / 1000.0); // Random step between -1.0 and 1.0
        double new_f = objectiveFunction(new_x);

        // Calculate change in objective function
        double delta_f = new_f - best_f;

        // Decide if we should accept the new solution
        if (delta_f < 0) {
            // Better solution found
            x = new_x;
            best_x = new_x;
            best_f = new_f;
        } else {
            // Accept worse solution with a certain probability
            double probability = exp(-delta_f / temp);
            if (rand() / (RAND_MAX + 1.0) < probability) {
                x = new_x;
            }
        }

        // Cool down
        temp *= 1 - cooling_rate;
    }

    return best_x;
}

int main() {
    double start_temp = 10000;   // Starting temperature
    double end_temp = 1;         // Ending temperature
    double cooling_rate = 0.01;  // Cooling rate
    double start_x = -10;        // Starting point

    double min_x = simulatedAnnealing(start_temp, end_temp, cooling_rate, start_x);
    std::cout << "Minimum x found: " << min_x << std::endl;
    std::cout << "Minimum value of f(x): " << objectiveFunction(min_x) << std::endl;

    return 0;
}
