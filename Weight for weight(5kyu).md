# Weight for weight
**no pass yeat**
## Instructions
My friend John and I are members of the "Fat to Fit Club (FFC)". John is worried because each month a list with the weights of members is published and each month he is the last on the list which means he is the heaviest.
I am the one who establishes the list so I told him: "Don't worry any more, I will modify the order of the list". It was decided to attribute a "weight" to numbers. The weight of a number will be from now on the sum of its digits.
For example 99 will have "weight" 18, 100 will have "weight" 1 so in the list 100 will come before 99. Given a string with the weights of FFC members in normal order can you give this string ordered by "weights" of these numbers?

### Example:
"56 65 74 100 99 68 86 180 90" ordered by numbers weights becomes: "100 180 90 56 65 74 68 86 99"
When two numbers have the same "weight", let us class them as if they were strings and not numbers: 100 is before 180 because its "weight" (1) is less than the one of 180 (9) and 180 is before 90 since, having the same "weight" (9) it comes before as a string.
All numbers in the list are positive numbers and the list can be empty.

### Notes
    Don't modify the input
    For C: The result is freed.
    
    
    
## Solution
```
function orderWeight(string) {
  var strArr = string.split(' ');
  var numArr = strArr.map(Number);
  var sumArr = strArr.map(function(item){
    item = item.split('').map(function(item2){
      return Number(item2);
    });
    return item.reduce(function(prev,cur){return prev+cur;});
  });
  for(var i=0; i<sumArr.length-1; i++){
    for(var j=i+1; j<sumArr.length; j++){
      if(sumArr[i]>sumArr[j]){
        var item = sumArr[i];
        sumArr[i] = sumArr[j];
        sumArr[j] = item;
        var item2 = numArr[i];
        numArr[i] = numArr[j];
        numArr[j] = item2;
      }else if(sumArr[i]==sumArr[j] && numArr[i] > numArr[j] && j!=i+1){      
        var item2 = numArr[i];
        numArr[i] = numArr[j];
        numArr[j] = item2;
      }
    }
  }
  return numArr.join(' ');
}
```

