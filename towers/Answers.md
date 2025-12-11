#  MCON 264 — Recursion Assignment: Towers of Hanoi × 3


##  Overview

In this lab, you implemented three recursive versions of the Towers of Hanoi problem and (optionally) one iterative version.  
Each part reinforces a key concept of recursion — base case, recursive case, and growth pattern — and illustrates how recursion can be refactored or replaced by iteration.

---

## Part 1 — Classic Towers of Hanoi (`TowersOfHanoi.java`)

### 1. Base Case
_Describe the base condition that stops recursion (for example, what happens when `n == 0`?)._

> best case is when n is 0, there are no disks to move so returns and does nothing.

### 2. Recursive Case
_Explain the sequence of recursive calls and what each represents._

> move n-1 disks to aux peg, move the largest disk to its destination then move 
> n-1 disks from aux to destination. 

### 3. Sample Trace (for n = 3)

| Move # | From | To |
|:------:|:----:|:--:|
|   1    |  A   | C  |
|   2    |  A   | B  |
|   3    |  C   | B  |
|   4    |  a   | c  |
|   5    |  b   | a  |
|   6    |  b   | c  |
|   7    |  a   | c  |


_Total moves = 2ⁿ − 1 = 7 (for n = 3)_

---

## Part 2 — Counting Moves (`TowersExercise21.java`)

### 1. Approach
_How did you modify the standard recursion to count rather than print moves?_

>  instead of printing each move or adding it to a list, using the variable count
> and incrementing it by 1 each time a disk was moved.

### 2. Verification of Formula
_Complete the table and verify that count = 2ⁿ − 1._

| n | Expected (2ⁿ − 1) | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 1 |       1        |       y        |
| 2 | 3 |       3        |       y        |
| 3 | 7 |       7        |       y        |
| 4 | 15 |       15       |       y        |
| 5 | 31 |       31       |       y        |

### 3. Reflection
_What changes when you replace printed moves with a counter? What are the pros and cons?_

> makes the program faster. because it doesn't have to print to the console/ store more strings.
> con is that you can't see the actual sequence of moves. 

---

## Part 3 — Hanoi Variation (`TowersVariations.java`)

### 1. New Rule
_Every move must pass through the middle peg. How does this alter the recursion?_

> so now moving a disk from peg 1 to peg 3 requrires two steps: 1-2, and 2-3. 
> this adds extra recursive calls to move disks back and forth.

### 2. Observed Move Counts

| n | Expected ≈ 3ⁿ − 1 | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 2 |       2        |       y        |
| 2 | 8 |       8        |       y        |
| 3 | 26 |       26       |       y        |
| 4 | 80 |       80       |       y        |

### 3. Analysis
_Why does this variation grow faster than the standard version? How do additional move constraints affect complexity?_

> grows faster because each move of the largest disk goes through the middle peg
> (2 moves instead of one). and have to move smaller disks back and forth more times.

---

## Comparative Analysis

### 1. Growth Patterns

| Version | Approx. Formula | Growth Type |
|:--|:--|:--|
| Standard | 2ⁿ − 1 | Exponential |
| Variation | 3ⁿ − 1 | Exponential (faster) |
| Iterative (Optional) | 2ⁿ − 1 | Same as recursive but loop based |

### 2. Stack Depth and Memory
_Estimate the maximum recursion depth before StackOverflowError and discuss how stack size (–Xss flag) affects this._

> max recursion is n (number of disks.) for large n (10k plus) you could get a 
> stackoverflow error since each recursive call uses stack memory. you can increase 
> size wiht the -xss flag for larger n values.

---

## Part 4 — Beyond Recursion (Extra Credit)

### Iterative / Explicit-Stack Version (`TowersIterative.java`)

1. How does your iterative version simulate recursion?
2. How did you track pending calls or frames?
3. Which version (r vs iterative) is clearer? Why?

> ✎ Your answer here

---

## Discussion &amp; Reflection

1. What three questions can you use to verify a recursive solution works?
2. How do the base case and recursive case cooperate to guarantee termination?
3. What is the trade-off between elegance and efficiency in recursion?

> 1. base case that stops recurstion. 2. does each recursive call move closer
> to the base case (n decreases)? 3. does the recursive case correctly solve the problem using smaller subproblems.
> 2. rc reduces the problem size. n becomes n-1 each time, and the base case stops when n reaches 0. gaurentees the recursion will eventually end as it gets closer to zero.
> 3. recursion is elegant and easy to understand (mostly) as it matches the problem structure naturally. it uses extra memory tho stack space, so it is often slower than iteration.

---

## References (APA or MLA format)

- Dale, N., Joyce, D., &amp; Weems, C. (2016). *Object-Oriented Data Structures Using Java* (Ch. 3 Recursion). Jones &amp; Bartlett.
- Additional videos or websites you consulted (YouTube CS50 Recursion, GeeksForGeeks Hanoi, etc.)

---

 **Submission Checklist**

- [✅] `TowersOfHanoi.java` — implemented and tested
- [✅] `TowersExercise21.java` — counts moves correctly
- [✅] `TowersVariations.java` — middle-peg constraint implemented
- [ ] (Extra Credit) `TowersIterative.java` — loop or explicit stack solution
- [✅] All JUnit tests pass (green on GitHub Actions)
- [✅] This `ANSWERS.md` file completed and committed to repo  
