# [Strip Url Params](https://www.codewars.com/kata/strip-url-params/train/javascript)

## Instructions

  Complete the method so that it does the following:

    * Removes any duplicate query string parameters from the url
    * Removes any query string parameters specified within the 2nd argument (optional array)

### Examples:

```
  stripUrlParams('www.codewars.com?a=1&b=2&a=2') // returns 'www.codewars.com?a=1&b=2'
  stripUrlParams('www.codewars.com?a=1&b=2&a=2', ['b']) // returns 'www.codewars.com?a=1'
  stripUrlParams('www.codewars.com', ['b']) // returns 'www.codewars.com'
```




## Solutions

```
  function stripUrlParams(url, paramsToStrip){
    var path = url.slice(0,url.indexOf('?'));
    var args = url.slice(url.indexOf('?'));
    paramsToStrip = paramsToStrip || [];
    if(!args) return url;
    var arr = args.match(/[?:\?|&]([^&#=]+)=([^&#=]+)/g);
    var keys = [];
    if(!arr) return url;
    arr.forEach(function(item){
      var key = item.slice(1,item.indexOf('='));
      if(keys.indexOf(key)===-1 && paramsToStrip.indexOf(key)===-1){
        keys.push(key);
        path = path+item;
      }
    });
    
    return path;
  }
```