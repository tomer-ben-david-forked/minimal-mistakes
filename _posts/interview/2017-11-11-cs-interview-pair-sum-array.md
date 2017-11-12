---
title: Find the pairs who sum to K
permalink: /cs-interview-array-pair-sum
published: false
---

# Programming Interview Question

## Array Pair Sum

1. array of size **n**
2. pairs which sum to number **k**

n, k

n <- 4, k <- 3

[1, 2, 3, 4] find all **pairs** of items which sum up to **3** k is 3!

[1, 2], [2, 1]

**Programming interview techniques / tips!**

1. array
   1. O(n), `n*lg(n)`

2. Integers

3. Sort it

4. Put them in hashmap

5. Pointers running over the array

## Java tips and tricks

1. `Arrays.sort` : Sorting an array in java - in place.
2. `Arrays.toString(arr)` : String representation of an array to print.

## Solutions

1. Brute force
2. Sorting, Pointers
3. HashMap / Set



```java
public class Main {

    public static void main (String[] args) {
        int k = 8;
        int[] arr = new int[] {1, 3, 5, 2, 6, 4, 4, 5, 6, 7, 8};
        Arrays.sort(arr);
        
        int p1 = 0;
        int p2 = arr.length - 1;
        
        while (p1 != p2) {
            int curSum = arr[p1] + arr[p2];
            if (curSum == k) {
                System.out.println("[" + arr[p1] + ", " + arr[p2] + "]");
                p1++;
            } else if (curSum < k) {
                p1++;
            } else if (curSum > k) {
                p2--;
            }
        }
    }

}

Standard Output
[1, 7]
[2, 6]
[3, 5]
[4, 4]
```

