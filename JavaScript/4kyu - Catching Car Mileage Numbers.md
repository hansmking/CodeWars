# [Catching Car Mileage Numbers](https://www.codewars.com/kata/catching-car-mileage-numbers/train/javascript)

## Instructions

  > "7777...8?!??!", exclaimed Bob, "I missed it again! Argh!" Every time there's an interesting number coming up, he notices and then promptly forgets. Who doesn't like catching those one-off interesting mileage numbers?

  Let's make it so Bob never misses another interesting number. We've hacked into his car's computer, and we have a box hooked up that reads mileage numbers. We've got a box glued to his dash that lights up yellow or green depending on whether it receives a 1 or a 2 (respectively).

  It's up to you, intrepid warrior, to glue the parts together. Write the function that parses the mileage number input, and returns a 2 if the number is "interesting" (see below), a 1 if an interesting number occurs within the next two miles, or a 0 if the number is not interesting.

  ### Note: ### In Haskell, we use No, Almost and Yes instead of 0, 1 and 2.

## "Interesting" Numbers

    Interesting numbers are 3-or-more digit numbers that meet one or more of the following criteria:

    * Any digit followed by all zeros: 100, 90000
    * Every digit is the same number: 1111
    * The digits are sequential, incementing†: 1234
    * The digits are sequential, decrementing‡: 4321
    * The digits are a palindrome: 1221 or 73837
    * The digits match one of the values in the awesomePhrases array

  > For incrementing sequences, 0 should come after 9, and not before 1, as in 7890.
  > For decrementing sequences, 0 should come after 1, and not before 9, as in 3210.

    So, you should expect these inputs and outputs:

```
    // "boring" numbers
    isInteresting(3, [1337, 256]);    // 0
    isInteresting(3236, [1337, 256]); // 0

    // progress as we near an "interesting" number
    isInteresting(11207, []); // 0
    isInteresting(11208, []); // 0
    isInteresting(11209, []); // 1
    isInteresting(11210, []); // 1
    isInteresting(11211, []); // 2

    // nearing a provided "awesome phrase"
    isInteresting(1335, [1337, 256]); // 1
    isInteresting(1336, [1337, 256]); // 1
    isInteresting(1337, [1337, 256]); // 2
```

### Error Checking

    
    * A number is only interesting if it is greater than 99!
    * Input will always be an integer greater than 0, and less than 1,000,000,000.
    * The awesomePhrases array will always be provided, and will always be an array, but may be empty. (Not everyone thinks numbers spell funny words...)
    * You should only ever output 0, 1, or 2.


## Solutions

```
  function isInteresting(number, awesomePhrases) {
    var num1 = number+1;
    var num2 = number+2;
    if(number==99||number==98){
      return 1;
    }else if(number.toString().length<3){
      return 0;
    }else{
      if(isPalindrome(number)||isIncre(number)||isDecre(number)||isAllZeros(number)||isSame(number)||isInArr(number,awesomePhrases)){
        return 2;
      }else if(isPalindrome(num1)||isIncre(num1)||isDecre(num1)||isAllZeros(num1)||isSame(num1)||isInArr(num1,awesomePhrases)||isPalindrome(num2)||isIncre(num2)||isDecre(num2)||isAllZeros(num2)||isSame(num2)||isInArr(num2,awesomePhrases)){
        return 1;
      }else{
        return 0;
      }
    }
  }

  function isPalindrome(n){
    var arr = String(n).split('');
    var isTrue = true;
    for(var i=0; i<arr.length; i++){
      isTrue = isTrue && (arr[i] === arr[arr.length-1-i]);
    }
    return isTrue;
  }

  function isIncre(n){
    var arr = String(n).split('');
    var isTrue = true;
    var nextNum;
    for(var i=0; i<arr.length-1; i++){
      nextNum = Number(arr[i])+1>9?0:Number(arr[i])+1;
      isTrue = isTrue && (nextNum === Number(arr[i+1]));
    }
    return isTrue;
  }

  function isDecre(n){
    var arr = String(n).split('');
    var isTrue = true;
    var nextNum;
    for(var i=0; i<arr.length-1; i++){
      nextNum = Number(arr[i])-1;
      isTrue = isTrue && (nextNum === Number(arr[i+1]));
    }
    return isTrue;
  }

  function isAllZeros(n){
    var len = String(n).length;
    return n%Math.pow(10,len-1)==0?true:false;
  }

  function isSame(n){
    var arr = String(n).split('');
    var isTrue = true;
    for(var i=1; i<arr.length; i++){
      isTrue = isTrue && (arr[0] === arr[i]);
    }
    return isTrue;
  }

  function isInArr(n,arr){
    var isTrue = false;
    for(var i=0; i<arr.length; i++){
      isTrue = isTrue || (n===arr[i]);
    }
    return isTrue;
  }
```

```
  function isInteresting(number, awesomePhrases) {
    if(number==99||number==98){
      return 1;
    }else if(number<98){
      return 0;
    }else{
      const tests = [
        (n)=>{ return /\d00+$/.test(n);},
        (n)=>{ return /^(\d)\1+$/.test(n);},
        (n)=>{ return RegExp(n).test(1234567890);},
        (n)=>{ return RegExp(n).test(9876543210);},
        (n)=>{ return String(n) == String(n).split('').reverse().join('');},
        (n)=>{ return awesomePhrases.some(function(a){return n==a;})}
      ];
      var ret = 0;
      tests.some(function(test){
        if(test(number)){
          return ret = 2; //防止继续判断其他规则
        }else if(test(number+1) || test(number+2)){
          ret = 1;
        }
      })
      return ret;
    }
  }
```