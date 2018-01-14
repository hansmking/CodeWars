# [Reverse polish notation calculator](https://www.codewars.com/kata/reverse-polish-notation-calculator/train/javascript)

## Instructions

  Your job is to create a calculator which evaluates expressions in 
  [Reverse Polish notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation).

  For example expression` 5 1 2 + 4 * + 3 - `(which is equivalent to` 5 + ((1 + 2) * 4) - 3 `in normal notation) should evaluate to 14.

  Note that for simplicity you may assume that there are always spaces between numbers and operations, e.g.` 1 3 + `expression is valid, but` 1 3+ `isn't.

  Empty expression should evaluate to 0.

  Valid operations are` +, -, *, / `.

  You may assume that there won't be exceptional situations (like stack underflow or division by zero).


## Solutions

```
  function calc(expr) {
    var arr = expr.split(' ');
    var popArr = [];
    var result;
    var num1=0,num2=0;
    var opArr = ['-','+','*','/'];
    for(var i=0; i<arr.length; i++){
      if(/^[0-9]+\.?[0-9]*$/.test(Number(arr[i]))){
        popArr.push(arr[i]);
      }else if(opArr.some(function(op){return op==arr[i]})){
        num1 = String(popArr.pop());
        num2 = String(popArr.pop());
        if(num1==0 && arr[i]=='/'){
          return popArr.push(0);
        }else{
          result = eval(num2.concat(arr[i],num1));
          popArr.push(result);
        }
      }else{
        popArr.push(0);
      }
    }
    return Number(popArr.pop());
  }
```