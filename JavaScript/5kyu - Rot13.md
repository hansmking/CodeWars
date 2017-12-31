# [Rot13](https://www.codewars.com/kata/rot13/train/javascript)

## Instructions
  ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

  Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

  Please note that using "encode" in Python is considered cheating.

### Example:
  rot13("test") //"grfg"
  rot13("Test") //"Grfg"
  
  
## Solution

```
function rot13(message){
  return message.replace(/[a-zA-Z]/g,function(l){
    if(l.charCodeAt()>90){
      return l.charCodeAt()>109? String.fromCharCode(l.charCodeAt()-13):String.fromCharCode(l.charCodeAt()+13);
    }else{
      return l.charCodeAt()>77? String.fromCharCode(l.charCodeAt()-13):String.fromCharCode(l.charCodeAt()+13);
    }
  })
}
```
```
  function rot13(message){
    return message.replace(/[a-zA-Z]{1}/g,function(l){
      var charCode = l.charCodeAt();
      if(charCode<91){
        if(charCode+13>90){
          charCode = 64+(charCode+13-90);
        }else{
          charCode = charCode+13;
        }
      }else{
        if(charCode+13>122){
          charCode = 96+(charCode+13-122);
        }else{
          charCode = charCode+13;
        }
      }
      return String.fromCharCode(charCode);
    })
  }
```

