# [Large Factorials](https://www.codewars.com/kata/large-factorials/train/javascript)

## Instructions

  In mathematics, the factorial of integer n is written as n!. It is equal to the product of n and every integer preceding it. For example: ` 5! = 1 x 2 x 3 x 4 x 5 = 120` 

  Your mission is simple: write a function that takes an integer n and returns the value of n!.

  You are guaranteed an integer argument. For any values outside the non-negative range, return null, nil or None (return an empty string "" in C and C++). For non-negative numbers a full length number is expected for example, return 25! = "15511210043330985984000000" as a string.

  For more on factorials, see [http://en.wikipedia.org/wiki/Factorial](http://en.wikipedia.org/wiki/Factorial)


## Solutions

#### My first solution (The execution time is too long.)

```
  function factorial(n){
    return n<=1?1:mul(n,factorial(n-1));
  }
  var mul = function(a,b){
    var bigNum = [String(a),String(b)];
    var proArr = [];
    var product = 0;
    bigNum = getMax(bigNum[0],bigNum[1]);
    var num1 = bigNum[0].split('');
    var num2 = bigNum[1].split('');
    for(var i=0;i<num1.length; i++){
      for(var j=0;j<num2.length;j++){
        var zeros = new Array(num1.length-1-i+num2.length-j).join('0');
        product = String(Number(num1[i])*Number(num2[j])).concat(zeros);
        proArr.push(product);
        product = 0;
      }
    }
    for(var k=0;k<proArr.length;k++){
      product = sum(product,proArr[k]);
    }
    return product;
  }

  var sum = function(a,b){
    var bigNum = [String(a),String(b)];
    var sumArr = [];
    var carry = 0;
    var sum = 0;
    bigNum = getMax(bigNum[0],bigNum[1]);
    var num1 = bigNum[0].split('');
    var num2 = bigNum[1].split('');
    if(num1.length>num2.length){
      var zeros = Array.apply(null, Array(num1.length-num2.length)).map(function(item, i) {
        return 0;
      });
      num2 = zeros.concat(num2);
    }
    for(var i=num1.length-1; i>-1; i--){
      sum = Number(num1[i])+Number(num2[i])+ carry;
      carry = parseInt(sum/10);
      sumArr.unshift(sum%10);
    }
    if(carry){
      sumArr.unshift(carry);
    }
    return sumArr.join('');
  }

  var getMax = function(a,b){
    var max = a,
        min = b;
    if(a.length<b.length){
      max = b;
      min = a;
    }else if(a.length == b.length){
      var i = 0;
      while(i<a.length){
        if(a.charAt(i)>b.charAt(i)){
          max = a;
          min = b;
          break;
        }else if(a.charAt(i)<b.charAt(i)){
          max = b;
          min = a;
          break;
        }else{
          i++;
        }
      }
    }
    return [max,min];
  }
```

#### Batter solution

```
  function factorial(n) {  
      var a = [1];  
      for (var i = 1; i <= n; i++) {  
          for (var j = 0, c = 0; j < a.length || c != 0; j++) {  
              var m = (j < a.length) ? (i * a[j] + c) : c;  
              a[j] = m % 10;  
              c = (m - a[j]) / 10;  
          }  
      }  
      return a.reverse().join("");  
  } 
```