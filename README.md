<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name:  Kousalya A  </h3>
<h3>Register Number:  212222230068       </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>


<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

## PROGRAM:
```py
import random
import string

# Target string
TARGET = "Artificial Intelligence"

# Fitness function (heuristic):
# Lower score = closer to target
def fitness(candidate):
    return sum(abs(ord(candidate[i]) - ord(TARGET[i])) for i in range(len(TARGET)))

# Generate a random string of same length as target
def random_string(length):
    letters = string.printable  # printable characters
    return ''.join(random.choice(letters) for _ in range(length))

# Mutate one character of the string
def mutate(parent):
    index = random.randrange(len(parent))  # pick a random index
    letters = string.printable
    new_char = random.choice(letters)
    # Replace char at the chosen index
    child = parent[:index] + new_char + parent[index+1:]
    return child

# Simple Hill Climbing Algorithm
def hill_climb():
    current = random_string(len(TARGET))     # Step 1: Random initial string
    current_score = fitness(current)

    print(f"Initial Score: {current_score} Solution: {current}")

    # Loop until fitness is zero
    while current_score != 0:
        neighbor = mutate(current)           # Step 2: Mutate
        neighbor_score = fitness(neighbor)   # Step 3: Evaluate

        # If neighbor is better, accept it
        if neighbor_score < current_score:
            current, current_score = neighbor, neighbor_score
            print(f"Score: {current_score} Solution: {current}")

    return current

# Run the algorithm
solution = hill_climb()
print("\nFinal Solution:", solution)

```

<hr>
<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence
<h2>Output:</h2>
<img width="452" height="177" alt="image" src="https://github.com/user-attachments/assets/2d24639d-89bc-4b40-abdc-56b015739955" />

<img width="351" height="165" alt="image" src="https://github.com/user-attachments/assets/52991656-3f71-4d86-b4b5-dd7826552e85" />

## RESULT:
 Thus the Simple Hill Climb Algorithm Implemented successfully.
