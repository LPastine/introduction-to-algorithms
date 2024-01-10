# Chapter 2 - Getting Started

## 2.1 Insertion sort

Input: A sequence of n numbers <a1, a2, ...an>
Output: A permutation (reordering) <a'1, a'2, ...a'n> of the
input sequence such that a'1 <= a'2 <= ... <= a'n

The numbers to be sorted are also known as the **keys**.

## 2.2 Analyzing algorithms

**Analyzing** an algorithm has come to mean predicting the resources that the algorithm requires.
You might consider resources such as memory, communication bandwidth, or energy consumption.
Most often, however, you'll want to measure computational time.

Most of this book assumes a generic one-processor RAM model of computation as the implementation
technology. In the RAM model, instructions execute one after another, with no concurrent
operations. It assumes that each instruction takes the same amount of time as any other instruction
and that each data access - using the value of a variable or storing into a variable - takes the same 
amount of time as any other data access.

In other words, in the RAM model each instruction or data access takes a constant amount
of time - even indexing into an array.

Although it is often straightforward to analyze an algorithm in the RAM model,
sometimes it can be quite a challenge. You might need to employ mathematical
tools such as combinatorics, probability theory, algebraic dexterity, and the ability
to identify the most significant terms in a formula. Because an algorithm might
behave differently for each possible input, we need a means for summarizing that
behavior in simple, easily understood formulas.

### Analysis of insertion sort

Instead of timing a run, or even several runs, of insertion sort, we can determine
how long it takes by analyzing the algorithm itself. We’ll examine how many times
it executes each line of pseudocode and how long each line of pseudocode takes
to run. We’ll first come up with a precise but complicated formula for the running
time. Then, we’ll distill the important part of the formula using a convenient notation
that can help us compare the running times of different algorithms for the
same problem.

To do so, we need to define the terms running time and input size more carefully.

The best notion for **input size** depends on the problem being studied. For many
problems, such as sorting or computing discrete Fourier transforms, the most natural
measure is the number of items in the input - for example, the number n of
items being sorted. For many other problems, such as multiplying two integers,
the best measure of input size is the total number of bits needed to represent the
input in ordinary binary notation. Sometimes it is more appropriate to describe the
size of the input with more than just one number. For example, if the input to an
algorithm is a graph, we usually characterize the input size by both the number of vertices
and the number of edges in the graph. We’ll indicate which input size measure
is being used with each problem we study.

The **running time** of an algorithm on a particular input is the number of instructions
and data accesses executed. How we account for these costs should be
independent of any particular computer, but within the framework of the RAM
model. For the moment, let us adopt the following view. A constant amount of
time is required to execute each line of our pseudocode. One line might take more
or less time than another line, but we’ll assume that each execution of the k th line
takes c k time, where c k is a constant. This viewpoint is in keeping with the RAM
model, and it also reflects how the pseudocode would be implemented on most
actual computers.

To highlight the order of growth of the running time, we have a special notation
that uses the Greek letter ‚ (theta). We write that insertion sort has a worst-case
running time of theta(n2) - pronounced "theta of n-squared" or just "theta n-squared".
We also write that insertion sort has a best-case running time of theta(n) - "theta of n"
or "theta n". For now, think of theta-notation as saying "roughly proportional when
n is large", so that theta(n2) means "roughly proportional to n2 when n is large".

## 2.3 Designing algorithms

### 2.3.1 The divide-and-conquer method

Many useful algorithms are **recursive** in structure: to solve a given problem, they
**recurse** (call themselves) one or more times to handle closely related subproblems.
These algorithms typically follow the **divide-and-conquer** method: they
break the problem into several subproblems that are similar to the original problem 
but smaller in size, solve the subproblems recursively, and then combine these
solutions to create a solution to the original problem.

In the divide-and-conquer method, if the problem is small enough - the **base
case** - you just solve it directly without recursing. Otherwise - the **recursive case** - 
you perform three characteristic steps:

1. **Divide** the problem into one or more subproblems that are smaller instances of the
   same problem.
2. **Conquer** the subproblems by solving them recursively.
3. **Combine** the subproblem solutions to form a solution to the original problem.

