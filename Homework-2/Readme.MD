## 1.1

State and prove a tight bound for the recurrence relation:
$$
T(n) = 5T\left(\frac{n}{3}\right) + n^2
$$

---

### Assumption
$$
T(n) = O(n^2)
$$

for some constant \( C > 0 \).

We proceed by substitution.

---

### Substitution 
Substitute the recurrence relation under the assumption:
$$
T(n) = 5T\left(\frac{n}{3}\right) + n^2
$$
Based on the assumption:
$$
T\left(\frac{n}{3}\right) \leq C\left(\frac{n}{3}\right)^2
$$
Substitute this into the original relation:
$$
T(n) \leq 5C\left(\frac{n}{3}\right)^2 + n^2
$$

---

### Simplify the Expression
Simplify the first term:
$$
5C\left(\frac{n}{3}\right)^2 = 5C\frac{n^2}{9}
$$
Thus:
$$
T(n) \leq \frac{5C}{9}n^2 + n^2
$$


$$
T(n) \leq n^2\left(\frac{5C}{9} + 1\right)
$$

---

### Bound \( C \)
$$
\frac{5C}{9} + 1 \leq C
$$
$$
1 \leq C - \frac{5C}{9}
$$
$$
1 \leq \frac{4C}{9}
$$
$$
C \geq \frac{9}{4}
$$

---

### Conclusion

$$
T(n) = O(n^2)
$$

---

### Final Tight Bound
The tight bound for the given recurrence relation is:
$$
T(n) = \Theta(n^2)
$$


## 1.2

### Subproblem Size and Tree Structure

The subproblem size for a node at depth \( i \) is:
$$
\frac{n}{5^i}.
$$

The tree has \( \log_5 n + 1 \) levels, and the total number of leaves is:
$$
3^{\log_2 n} = n^{\log_2 3}.
$$

---

### Total Cost at Each Level

The total cost for all nodes at level \( i \), where \( i = 0, \dots, \log_5 n - 1 \), is:
$$
3^i \left( \frac{n}{5^i} \right) = \left( \frac{3}{5} \right)^i n.
$$

---

### Total Cost of the Recursion Tree

The total cost \( T(n) \) is the sum of all levels plus the work at the leaves:
$$
T(n) = n + \frac{3}{5}n + \left( \frac{3}{5} \right)^2 n + \dots + \left( \frac{3}{5} \right)^{\log_2 n - 1} n + \Theta\left( n^{\log_2 3} \right).
$$

This can be expressed as a summation:
$$
T(n) = \sum_{i=0}^{\log_2 n - 1} \left( \frac{3}{5} \right)^i n + \Theta\left( n^{\log_2 3} \right).
$$

---

### Infinite Series Bound

The total cost for all nodes at level \( i \) is:
$$
\text{Cost} = \sum_{i=0}^{\log_5 n - 1} \left( \frac{3}{5} \right)^i n.
$$

To bound this summation, we consider an infinite geometric series:
$$
\sum_{i=0}^{\infty} r^i = \frac{1}{1 - r} \quad \text{for } |r| < 1.
$$

Here, \( r = \frac{3}{5} \). Thus:
$$
\sum_{i=0}^{\infty} \left( \frac{3}{5} \right)^i = \frac{1}{1 - \frac{3}{5}} = \frac{1}{\frac{2}{5}} = \frac{5}{2}.
$$

Since the summation for a finite series  is smaller than this bound:
$$
\sum_{i=0}^{\log_5 n - 1} \left( \frac{3}{5} \right)^i \leq \frac{5}{2}.
$$

---

### Total Cost Bound

Substitute back into the total cost:
$$
T(n) \leq n \cdot \sum_{i=0}^{\log_5 n - 1} \left( \frac{3}{5} \right)^i + \Theta\left( n^{\log_2 3} \right).
$$

Using the infinite series bound:
$$
\sum_{i=0}^{\log_5 n - 1} \left( \frac{3}{5} \right)^i \leq \frac{5}{2}.
$$

Thus:
$$
T(n) \leq n \cdot \frac{5}{2} + \Theta\left( n^{\log_2 3} \right).
$$

the final bound is:
$$
T(n) = \Theta\left( n^{\log_2 3} \right).
$$

## 2


### The recurrence relation is:

$$
T(n) = T\left(\frac{n}{4}\right) + T\left(\frac{3n}{4}\right) + cn
$$

---

### Using substitution method


$$
T(n) \leq c \left( \frac{n}{4} \log \frac{n}{4} \right) + c \left( \frac{3n}{4} \log \frac{3n}{4} \right) + cn
$$

---

### Simplify the logarithmic terms

$$
\log \frac{n}{4} = \log n - \log 4, \quad \log \frac{3n}{4} = \log n + \log 3 - \log 4
$$

Substitute these into the recurrence:

$$
T(n) \leq c \left[ \frac{n}{4} (\log n - \log 4) \right] + c \left[ \frac{3n}{4} (\log n + \log 3 - \log 4) \right] + cn
$$

---

### Combine the terms


$$
T(n) \leq c \left[ \frac{n}{4} \log n - \frac{n}{4} \log 4 + \frac{3n}{4} \log n + \frac{3n}{4} \log 3 - \frac{3n}{4} \log 4 \right] + cn
$$



$$
\frac{n}{4} + \frac{3n}{4} = n
$$

Thus:

$$
T(n) \leq c \left[ n \log n - n \left( \frac{\log 4}{4} + \frac{3 \log 4}{4} \right) + \frac{3n}{4} \log 3 \right] + cn
$$

---

### Dominant aerm analysis

As n grows to infinity:

$$
T(n) \leq cn \log n + \text{lower order terms}.
$$

---

### Final result

The solution to the recurrence is:

$$
T(n) = O(n \log n).
$$


## 3

 
The proof claims that at each level of recursion, the total work is O(n), and this holds for O(log n) levels.  
But the algorithm performs 4 recursive calls at each level, not a constant O(n) work per level.

---


The recurrence relation for the algorithm is:

$$
T(n) = 4T\left(\frac{n}{2}\right) + O(n).
$$

---

- 4 Recursive Calls: At each level, the problem is divided into 4 subproblems, each of size \( n/2 \).  
- Linear Work: Outside of the recursion \( O(n) \).

---

Using the Master Theorem:

$$
T(n) = aT\left(\frac{n}{b}\right) + f(n),
$$




$$
a = 4 \quad \text{and} \quad b^d = 2^1 = 2.
$$


$$
T(n) = O\left(n^{\log_b a}\right) = O\left(n^{\log_2 4}\right).
$$


$$
T(n) = O(n^2).
$$

## 4.1

    function find_occurrences_bruteforce(nums, target):
        indices = []  

        for i from 0 to length(nums) - 1:
            if nums[i] == target:
                append i to indices
            else if nums[i] > target:
                break  # Exit the loop as the rest of the list is irrelevant (sorted list)

        if indices is empty:
            return -1
        else:
            return (indices[0], indices[-1])  # First and last indices of the target


## 4.2

### Binary Search 




    function binsearch(nums, target, leftbias):
        l = 0                # Left boundary
        r = length(nums) - 1 # Right boundary
        i = -1               # Default result if target is not found

        while l <= r:
            m = (l + r) // 2  # Midpoint of the search range

            if nums[m] < target:
                l = m + 1     # Move to the right half
            else if nums[m] > target:
                r = m - 1     # Move to the left half
            else:
                i = m         # Target found; update potential result
                if leftbias:
                    r = m - 1 # Move left to find leftmost target
                else:
                    l = m + 1 # Move right to find rightmost target

        return i
    

## 5.1


    # Assume we have a list of applicants called walkers
    # Each element in walkers is either "experienced" or "new"
    # We know there are strictly more experienced walkers than new ones.

    # Function to perform an evaluation:
    # Given two walkers, walker1 and walker2:
    # - If walker1 is experienced, return "experienced" if walker2 is experienced, else "new".
    # - If walker1 is new, return "experienced" or "new" arbitrarily (unreliable).

    FUNCTION Evaluate(walker1, walker2):
        IF walker1 == "experienced":
            IF walker2 == "experienced":
                RETURN "experienced"
            ELSE:
                RETURN "new"
        ELSE:
            # walker1 is new; unreliable evaluation
            RETURN random choice of ["experienced", "new"]

    FUNCTION Identify(walkers):
        # Initialize vote counts for each walker
        LET votes = dictionary mapping i -> 0 for i in [0 .. length(walkers)-1]

        # For each pair of distinct walkers (j, i):
        FOR i IN 0 TO length(walkers)-1:
            FOR j IN 0 TO length(walkers)-1:
                IF i == j:
                    CONTINUE
                result = Evaluate(walkers[j], walkers[i])
                IF result == "experienced":
                    votes[i] = votes[i] + 1

        # If a walker receives more than half of the votes as "experienced",
        # it means that the majority of experienced walkers have identified them as such.
        LET experienced_walkers = EMPTY_LIST
        FOR (i, count) IN votes:
            IF count > (length(walkers) / 2):
                ADD walkers[i] TO experienced_walkers

        RETURN experienced_walkers

## 5.2

 

     Define Identify_Improved(walkers):
     Input: A list of walkers.
     Output: A reduced list of walkers containing more experienced individuals.

     Initialize an empty list exp_walkers to store the selected walkers.

     Iterate over the walkers list in steps of 2 (to process pairs):
     For each pair of walkers walkers[i] and walkers[i+1]:
        - Perform evaluation using evaluate(walkers[i], walkers[i+1]).
        - If the result of the evaluation is "experienced":
        - Append walkers[i+1] to the exp_walkers list.
        - Otherwise:
        - Append walkers[i] to the exp_walkers list.

     Return the exp_walkers list.


## 5.4


    . Define find_experienced_walker(walkers):
    - Input: A list of walkers.
    - Output: A single experienced walker.

    . Base Case:
    - If the length of the walkers list is 1:
        - Return the single walker.

    . Recursive Step:
    - Use the Identify_Improved procedure (5.3) to reduce the group size:
        - Pass the current list of walkers to Identify_Improved.
        - Store the resulting reduced list in a variable reduced_walkers.

    . Recursive Call:
    - Call find_experienced_walker on reduced_walkers.
    - Return the result of the recursive call.

## 5.5

Base Case (n=1):  
If \( n = 1 \), then there is only one applicant. The problem states that strictly more than \( n/2 \) applicants are experienced. Since there is only one applicant, that applicant must be experienced. The algorithm returns the single applicant, which is experienced. 

Inductive Hypothesis:  
Assume that for all \( k < n \), if we run the algorithm on \( k \) applicants (with strictly more than \( k/2 \) experienced), the algorithm returns a single experienced walker.

Inductive Step (for k = n):  
Given \( n \) applicants with strictly more than \( n/2 \) experienced:

1. The algorithm uses the procedure from Parts 5.2 and 5.3 to reduce the input size from \( n \) applicants to a smaller subset of size \( m \), where \( 0 < m <= n/2 \).

2. By the correctness of the reduction procedure (as proven in Parts 5.2 and 5.3), this smaller subset of size \( m \) still has strictly more than \( m/2 \) experienced applicants.

3. Now we have a problem of size \( m \), where \( m < n \) and strictly more than \( m/2 \) are experienced. By the inductive hypothesis, the algorithm correctly finds a single experienced walker in this smaller instance.

4. Since the algorithm’s step at size \( n \) reduces the problem to a smaller instance that we know is solved correctly, the algorithm for size \( n \) also returns an experienced walker.



## 5.6

 The recurrence relation is:
$$
T(n) = T\left(\frac{n}{2}\right) + O(n)
$$
Base Case:
$$
T(1) = 1
$$
By inductive hypothesis and substitution method:
$$
T(n) \leq c \cdot n
$$
$$
T(n) \leq T\left(\frac{n}{2}\right) + c’ \cdot n
$$
$$
T\left(\frac{n}{2}\right) \leq c \cdot \frac{n}{2}.
$$
$$
T(n) \leq c \cdot \frac{n}{2} + c’ \cdot n.
$$
$$
T(n) \leq \left(\frac{c}{2} + c’\right) \cdot n.
$$
$$
\frac{c}{2} + c’ \leq c.
$$
$$
c’ \leq \frac{c}{2}.
$$
$$
c \geq 2 \cdot c’.
$$

$$
T(n) = O(n).
$$


## 5.7


### Find one known experienced walker:  
   Using the recursive funtion from 5.4, we first detect a single experienced walker. This procedure repeatedly halves the number of applicants while maintaining the property that strictly more than half are experienced. At the end, we end up with a single walker who must be experienced. This takes O(n) evaluations as shown in 5.6.

### Using the known experienced walker to classify other walkers:  
   Once we have identified one experienced walker, we use it as an evaluator. Since an experienced walker always tells the truth, we have this walker evaluate every other applicant exactly once. If our known experienced walker says that another applicant is experienced, then that walker is indeed experienced; if they say new, then that wlaker is new.

Because each applicant is evaluated only once by the known experienced walker, this classification step also uses O(n) evaluations.

Total Evaluations:  
- O(n) evaluations to find the single known experienced walker.
- O(n) evaluations to classify all remaining applicants.

The total running time is in order of O(n).
