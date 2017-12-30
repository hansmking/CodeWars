# [WeIrD StRiNg CaSe](https://www.codewars.com/kata/weird-string-case/train/javascript)

## Instuctions

  Write a function toWeirdCase (weirdcase in Ruby) that accepts a string, and returns the same string with all even indexed characters in each word upper cased, and all odd indexed characters in each word lower cased. The indexing just explained is zero based, so the zero-ith index is even, therefore that character should be upper cased.

  The passed in string will only consist of alphabetical characters and spaces(' '). Spaces will only be present if there are multiple words. Words will be separated by a single space(' ').

  ### Examples:
```
  toWeirdCase( "String" );//=> returns "StRiNg"
  toWeirdCase( "Weird string case" );//=> returns "WeIrD StRiNg CaSe"
```

    
## Solution

```
  function toWeirdCase(string){
    var arr = string.split(' ');
    var arrSub = [];
    for(var i=0; i<arr.length; i++){
      arrSub=arr[i].split('');
      for(var j=0; j<arrSub.length; j++){
        if(j%2){
          arrSub[j] = arrSub[j].toLowerCase();
        }else{
          arrSub[j] = arrSub[j].toUpperCase();
        }
      }
      arr[i]=arrSub.join('');
    }
    return arr.join(' ');
  }
```

