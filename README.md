# BaekJoon-11866-JosephusProblem
Efficient implementation of JosephusProblem


## Josephus Problem
Josephus problem is a sequence in which a group of N people surrounding a circle are eliminated. The sequence is as follows. A group of N people sits around a circular table, and k-th person is removed until everyone is eliminated. The sequence in whice the k-th person is removed is called the Josephus permutation. The Josephus problem is the process of finding the Josephus permutation.


## In BaekJoon-11866...
Given variations K and N in first line.
Program output is Josephus permutation for variation N and N

### Example
  Input : 7 3

  Output: <3, 6, 2, 7, 5, 1, 4>


## Normal solution
Use a queue, one of the data structures. 

If this index is ship of K, Pop data in queue. And shift all element before pop data index to right. Repeat this process to everyone eliminated.

But this process have square of timecomplication.

Therefore, I suggest another way.

## ‼️My solution

### Normal solution's problems
  #### First. A function of pop needs to receive for a variable K.
    Function of pop needs a variable K for pop k-th data in queue.

  #### Second. A function of push needs to receive for a variable index
    Function of push need a variable for shift data.


### Concept
  I don't override function. Functions work that receive only sturct.

  
