# [Human Readable Time](https://www.codewars.com/kata/human-readable-time/train/javascript)

## Instuctions

  Write a function, which takes a non-negative integer (seconds) as input and returns the time in a human-readable format (HH:MM:SS)

    *  HH = hours, padded to 2 digits, range: 00 - 99
    *  MM = minutes, padded to 2 digits, range: 00 - 59
    *  SS = seconds, padded to 2 digits, range: 00 - 59

  The maximum time never exceeds 359999 (99:59:59)

  You can find some examples in the test fixtures.
    
    
## Solution

```
  function humanReadable(seconds) {
    var ss = seconds%60;
    var mm = parseInt(seconds/60)%60;
    var hh = parseInt(seconds/3600);
    if(ss<10){ss='0'+ss}
    if(mm<10){mm='0'+mm}
    if(hh<10){hh='0'+hh}
    return hh+':'+mm+':'+ss;
  }
```

