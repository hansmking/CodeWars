# [Split Strings](https://www.codewars.com/kata/split-strings/train/javascript)

## Instuctions

  Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore ('_').

### Examples:

```
  solution('abc') // should return ['ab', 'c_']
  solution('abcdef') // should return ['ab', 'cd', 'ef']
```


    
## Solution

```
  function solution(str){
    var arr = str.split('');
    var arrLen = arr.length;
    var arr2 = [];
    var arr3 = [];
    if(arrLen%2==1 ){
      arr.push('_');
    }
    if(arrLen == 0){
      return arr2;
    }else{
      for(var i=0; i<arrLen; i=i+2){
        arr2.push(arr[i]+arr[i+1]);
      }
      return arr2;
    }
  }
```

```
  function solution(str){
    return str.concat('_').match(/../g);
  }
```

