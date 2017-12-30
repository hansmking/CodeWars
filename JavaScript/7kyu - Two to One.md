# [Two to One](https://www.codewars.com/kata/two-to-one/train/javascript)

## Instructions
  
  Take 2 strings s1 and s2 including only letters from ato z. Return a new sorted string, the longest possible, containing distinct letters,

  each taken only once - coming from s1 or s2. 

  ### Examples:

``` 
  a = "xyaabbbccccdefww" b = "xxxxyyyyabklmopq" longest(a, b) -> "abcdefklmopqwxy"
  a = "abcdefghijklmnopqrstuvwxyz" longest(a, a) -> "abcdefghijklmnopqrstuvwxyz" 
```



  
## Solution

```
  function longest(s1, s2) {
    s1 = s1+s2;
    s1 = s1.split('');
    s1 = s1.sort();
    var item = s1[0];
    var arr = [item];
    for(var i=1;i<s1.length;i++){
      if(s1[i]!=item){
        arr.push(s1[i]);
        item = s1[i];
      }
    }
    return arr.join('');
  }

```

