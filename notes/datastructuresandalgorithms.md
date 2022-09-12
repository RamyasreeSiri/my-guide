# Data structures and Algorithms

## Topics to cover

Time and Space complexity

## Quiz

* Define a function which adds two numbers and returns the result after given time using promises

 <details>
 <summary>Solution</summary>

 function timer(n) {
   return new Promise((resolve) => setTimeout(resolve, n));
 }
 async function add(a, b) {
   await timer(500);
   return a+b;
 }
 (async function() {
 console.log(await add(2,3));
 })()
 </details>

<!-- tooltips -->
*[JVM]: Java Virtual Machine
<!-- tooltips end -->

## Documentation / Specification

[Book The introduction to algorithms](https://docs.google.com/viewer?a=v&pid=sites&srcid=ZGVmYXVsdGRvbWFpbnxhbGdvcml0aG1zaWNzMzUzfGd4OjI3ZjYxZjM3MmI1NGNhNmU)

## Notes

1️⃣🚩Reference
[The Last Algorithms Course You'll Need by ThePrimeagen Course](https://frontendmasters.com/workshops/algorithms/)
[The Last Algorithms Course You'll Need by ThePrimeagen Resources](https://github.com/ThePrimeagen/fem-algos/tree/main/lessons)

### What is Big O?

* Big O is a way to categorize your algorithms time or memory requirements based on input. It is not meant to be an exact measurement. It will not tell you how many CPU cycles it takes, instead it is meant to generalize the growth of your algorithm.

* other way of saying it **As your input grows how fast does your computation or memory grow?**

O(N) - they mean your algorithm will grow linearly based on input.

### **Important Concepts**

 1. Growth is with respect to input
 2. Constants are dropped

  <details>
    <summary>Explanation</summary>
    O(2N) -> O(N) and this makes sense. That is because Big O is meant to describe the upper bound of the algorithm (the growth of the algorithm). The constant eventually becomes irrelevant.

    Take the following:

    N = 1, O(10N) = 10, O(N^2) = 1

    N = 5, O(10N) = 50, O(N^2) = 25

    N = 100, O(10N) = 1,000, O(N^2) = 10,000 // 10x bigger

    N = 1000, O(10N) = 10,000, O(N^2) = 1,000,000 // 100x bigger

    N = 10000, O(10N) = 100,000, O(N^2) = 100,000,000 // 1000x bigger
  </details>

  3. Worst case is usually the way we measure,

#### Example 1

> *Important concept* 1: Growth is with respect to input

What is the running time of this code?

```typescript
  function sum_char_codes(n: string): number {
      let sum = 0;
      for (let i = 0; i < n.length; ++i) {
          sum += n.charCodeAt(i);
      }

      return sum;
  }
```

* The running time is O(N), can be told based on for every unit increase in input, there is to be one more loop, so its a linear relation between input and execution.

> Simplest **🟡trick** for complexity, look for loops, where do you loop over the inputs

#### Example 2

> *Important concept* 2. Constants are dropped

What is the running time of this code?

```typescript
  function sum_char_codes(n: string): number {
      let sum = 0;
      for (let i = 0; i < n.length; ++i) {
          sum += n.charCodeAt(i);
      }

      for (let i = 0; i < n.length; ++i) {
          sum += n.charCodeAt(i);
      }

      return sum;
  }
```

* The running time is O(2N), as we are looping over the input length twice, but as we are dropping constants because it becomes irrelevant in the long run. So **O(2N) to O(N)**.

#### Example 3

> *Important concept* 3. Worst case is usually the way we measure,

What is the running time of this code?

```typescript
  function sum_char_codes(n: string): number {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
      const charCode = n.charCodeAt(i);
      // Capital E
      if (charCode === 69) {
        return sum;
      }

      sum += charCode;
    }

    return sum;
  }
```

* The running time is O(N), as the character could be at the start or middle or end, so we take the worst case measure which is O(N).

[Source](https://www.hackerearth.com/practice/notes/big-o-cheatsheet-series-data-structures-and-algorithms-with-thier-complexities-1/)
![Big O Notation](../images/algorithmsanddatastructures/big-o-complexity.png)

#### Some examples

##### O(1)

```typescript
function get_char_at(n: string, index): number {
  return n[index]; // n + width * offset => n + 32bytes * index
}
```

##### O(N^2)

```typescript
function sum_char_codes(n: string): number {
  let sum = 0;
  for (let i = 0; i < n.length; ++i) {
      for (let j = 0; j < n.length; ++j) {
          sum += charCode;
      }
  }

  return sum;
}
```

##### O(N^3)

```typescript
function sum_char_codes(n: string): number {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
        for (let j = 0; j < n.length; ++j) {
            for (let k = 0; k < n.length; ++k) {
                sum += charCode;
            }
        }
    }
    return sum;
}
```

##### O(n log n)

* Quicksort (we will implement and explain)

##### O(log n)

* Binary search trees

##### O(sqrt(N))

### Data structure

#### What is an Array?

const a = []

* They are fixed size, contiguous memory chunks

* That means you cannot grow it
* There is no "insertAt" or push or pop. Doesn't mean you can't write those though

### Algorithms

#### Search

##### Linear Search

```typescript
function get_char_index(n: string, character): number {
  for (let i = 0; i < n.length; ++i) {
    if(n[i] === character) {
      return i;
    }
  }
  return -1;
}
```

* O(N)

### Algorithm implementation practice repo

[Kata](https://github.com/ThePrimeagen/kata-machine)

```
> git clone git@github.com:ThePrimeagen/kata-machine.git
> cd kata-machine
> yarn install
> yarn generate
> navigate to day1 folder
```

> tryout: `algorithms/fm-theprimeagen-kata-machine`

> **🟡trick** if the inputs halves at each step, its likely O(LogN) or O(NLogN)

1. LinearSearchList
2. BinarySearchList
3. TwoCrystalBalls problem
4. BubbleSort
5. DoublyLinkedList
6. Queue
7. QuickSort


*Bubble sort* - is a simple sorting algorithm that compares a pair of adjacent elements in a list. If an element is not in the right order, we swap the element with the one before.
*LinkedList* - The data structure will have a node, a header pointer, a tail pointer - node has a value, and next node pointer
*DoublyLinkedList* - The data structure will have node, prev node pointer, head pointer, tail pointer - node has a value, and next node pointer.
*Queue* - data structure on top of a linked list, first in - first out
*Stack* - data structure on top of a linked list, first in - last out
*ArrayBuffer* - set value of length, and when inserting more than the capacity, copy over everything and create a new array with more capacity
*RingBuffer* - fill the positions in a continuous manner and when all is filled, copy it over to new array and continue
*QuickSort* - have a pivot and move the values to either low of pivot or hight of pivot and pick a new pivot in low and high values by excluding the previous pivot and continue this till only one element is in the array.

### Recursion

* A function that calls itself until the problem is solved. This usually involves what is referred to as a base case. A base case is the point in which the problem is solved.
* Know the base case and add it before recusing step.

```typescript
// foo adds from 1 to n
function foo(n: number): number {
    // Base Case
    if (n === 1) {
        return 1;
    }

    // We shall Recurse!
    return n + foo(n - 1);
}
```