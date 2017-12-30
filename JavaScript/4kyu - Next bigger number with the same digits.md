# Next bigger number with the same digits

## Instructions

  You have to create a function that takes a positive integer number and returns the next bigger number formed by the same digits:

  ```
  nextBigger(12)==21
  nextBigger(513)==531
  nextBigger(2017)==2071
  ```
  If no bigger number can be composed using those digits, return -1:

  ```
  nextBigger(9)==-1
  nextBigger(111)==-1
  nextBigger(531)==-1
  ```

## Solutions

```
  function nextBigger(n){
    var nArr = n.toString().split('');
    if(nArr.length<2){
      return -1;
    }
    for(var i=nArr.length-2; i>-1; i--){
      for(var j=nArr.length-1; j>i; j--){
        if(nArr[j]>nArr[i]){
          var num = nArr[i];
          nArr[i] = nArr[j];
          nArr[j] = num;
          return parseInt((nArr.slice(0,i+1).concat(nArr.slice(i+1).sort())).join(''));
        }
      }
    }
    return -1;
  }
```