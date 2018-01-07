# [IP Validation](https://www.codewars.com/kata/ip-validation/train/javascript)

## Instructions

  Write an algorithm that will identify valid IPv4 addresses in dot-decimal format. IPs should be considered valid if they consist of four octets, with values between 0..255 (included).

  Input to the function is guaranteed to be a single string.

### Examples
```
  // valid inputs:
  1.2.3.4
  123.45.67.89

  // invalid inputs:
  1.2.3
  1.2.3.4.5
  123.456.78.90
  123.045.067.089
```
#### Note: leading zeros (e.g. 01.02.03.04) are considered not valid in this kata!


## Solutions

```
  function isValidIP(str) {
    var arr = str.split('.');
    var isTrue = true;
    var arrItem = null;
    if(arr.length == 4){
      arr.map(function(item){
        arrItem = item.match(/(^[0]$)|(^[1-9][0-9]*$)/);
        if(arrItem == null){
          isTrue = isTrue && false;
        }else{
          arrItem = arrItem[0];
          isTrue = isTrue && (arrItem>=0 && arrItem<=255);
        }
      });
    }else{
      isTrue = false;
    }
    return isTrue;
  }
```

### BETTER:

```
  function isValidIP(str) {
    return /^(([1-9]?\d|1\d\d|2[0-4]\d|25[0-5])(\.(?!$)|$)){4}$/.test(str);
  }
```