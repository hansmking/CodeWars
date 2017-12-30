# [Find the smallest integer in the array](https://www.codewars.com/kata/find-the-smallest-integer-in-the-array/train/javascript)

## Instructions
  
  Given an array of integers your solution should find the smallest integer.

  ### For example:

    > Given [34, 15, 88, 2] your solution will return 2
    > Given [34, -345, -1, 100] your solution will return -345

  You can assume, for the purpose of this kata, that the supplied array will not be empty.


  
## Solution

```
  class SmallestIntegerFinder {
    findSmallestInt(args) {
      var min = Math.min.apply(null,args);
      return min;
    }
  }
```

