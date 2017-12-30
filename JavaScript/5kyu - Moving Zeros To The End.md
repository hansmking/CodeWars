# [Moving Zeros To The End](https://www.codewars.com/kata/moving-zeros-to-the-end/train/javascript)

## Instructions
  
  Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.

```
  moveZeros([false,1,0,1,2,0,1,3,"a"]) // returns[false,1,1,2,1,3,"a",0,0]
```
  
## Solution

```
  const moveZeros = function (arr) {
    let cont = arr.length;
    for(let i=0;i<cont;i++){
        if(arr[i]===0){
          arr.splice(i,1);
          arr.push(0);
          i--;
          cont--;
        }
    }
    return arr; 
  }
```

