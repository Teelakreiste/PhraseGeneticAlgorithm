# Genetic Algorithm - Phrase Evolution
Code was based on and adapted from [Nature of Code](https://natureofcode.com/book/chapter-9-the-evolution-of-code/).

This code implements a Genetic Algorithm to evolve a population of individuals to match a target phrase. The algorithm mimics the process of natural selection and genetic inheritance to find the best solution.

## Algorithm Overview

1. **Initialization**: Create an initial population of individuals with random genes.
2. **Fitness Calculation**: Calculate the fitness of each individual by comparing its genes to the target phrase.
3. **Selection**: Select individuals for reproduction based on their fitness, using a weighted probability selection method.
4. **Crossover**: Create offspring by performing crossover between pairs of selected parents, combining their genes to create new individuals.
5. **Mutation**: Introduce random changes (mutations) in the genes of the offspring to maintain diversity in the population.
6. **Fitness Evaluation**: Calculate the fitness of the new individuals.
7. **Replacement**: Replace the old generation with the new generation of offspring.
8. **Termination**: Repeat steps 3-7 until the target phrase is found or a termination condition is met.
9. **Results**: Output the best phrase found and the number of generations required to reach it.

## Classes

### `DNA`

Represents an individual in the population.

#### Properties

- `target`: The target phrase to match.
- `genes`: The genes (characters) of the individual.
- `fitness`: The fitness score of the individual.

#### Methods

- `calculate_fitness()`: Calculates the fitness of the individual based on the number of matching genes with the target phrase.
- `crossover(partner)`: Performs crossover with another individual to create a child with a combination of genes from both parents.
- `mutate(mutation_rate)`: Randomly mutates the genes of the individual with a given mutation rate.
- `get_phrase()`: Returns the string representation of the individual's genes.

### `Population`

Represents a population of individuals.

#### Properties

- `target_phrase`: The target phrase to match.
- `total_population`: The total number of individuals in the population.
- `mutation_rate`: The probability of mutation for an individual.
- `population`: A list of `DNA` objects representing the population.
- `generation`: The current generation number.
- `best_fitness`: The fitness of the best individual.
- `best_phrase`: The best phrase found in the population.
- `average_fitness_history`: A list to store the average fitness over generations.
- `best_fitness_history`: A list to store the best fitness over generations.

#### Methods

- `calculate_fitness()`: Calculates the fitness of each individual in the population.
- `selection()`: Selects individuals for reproduction based on their fitness.
- `reproduction(mating_pool)`: Performs reproduction by creating new individuals through crossover and mutation.
- `evolve()`: Evolves the population until the target phrase is found or a termination condition is met.
- `display_progress()`: Displays the current generation, best phrase, best fitness, and average fitness.
- `plot_fitness_progress()`: Plots the progress of the best fitness over generations.
- `calculate_average_fitness()`: Calculates the average fitness of the population.
- `plot_average_fitness()`: Plots the progress of the average fitness over generations.

## Usage

1. Set the parameters for the Genetic Algorithm: `target_phrase`, `mutation_rate`, and `total_population`.
2. Create an instance of the `Population` class with the specified parameters.
3. Call the `evolve()` method to start the evolution process.
4. After the algorithm finishes, print the best phrase found and the total number of generations.
5. Optionally, use the `plot_fitness_progress()` and `plot_average_fitness()` methods to visualize the progress of the best fitness and average fitness over generations.

```python
# Parameters for the Genetic Algorithm
target_phrase = "BACK TO THE FUTURE"
mutation_rate = 0.01
total_population = 150

# Create a population instance and evolve
population = Population(target_phrase, total_population, mutation_rate)
population.evolve()

print("Algorithm finished!")
print("Best phrase:", population.best_phrase)
print("Total generations:", population.generation)

# Plot the progress of the best fitness and average fitness
population.plot_fitness_progress()
population.plot_average_fitness()
