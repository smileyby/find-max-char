前端群测试题
===========

## 随机字符串找出其中出现最多的一个字符

方法1：

```js

var str = 'asdfssaaasasasasaa';
var length = str.length;

// 去重
function onlystr(str){
  var newStr = '';
  for(var i = 0;i < length; i += 1){
    if(newStr.indexOf(str[i]) === -1){
      newStr += str[i];
    }
  }
  return newStr;
};

var onlyStr = onlystr(str);

// 变数组,取长度，最长则最多
function getMaxLength(onlyStr, str){
  var maxABC = '';
  var maxlength = 0;
  var length = onlyStr.length;
  for(var j = 0;j < length; j += 1){
    var thisLength = str.split(onlyStr[j]).length;
    if(maxlength < thisLength){
      maxABC = onlyStr[j];
      maxlength = thisLength;
    }
  };
  return maxABC;
};

var max = getMaxLength(onlyStr, str);
console.log('maxABC: ' + max);

```

方法2：

```js

var str = 'ssfffadfssaaasasasasaa';
function getMax(str){
  var newStr = '';
  var arr = [];
  var index = 0;
  var length = str.length;
  for(var i = 0;i < length; i += 1){
    if(newStr.indexOf(str[i]) === -1){
      newStr += str[i];
      arr[index] = 1;
      index += 1;
    }else{
      arr[newStr.indexOf(str[i])] += 1;
    };
  };
  var maxNum = Math.max.apply(null, arr);
  var maxABC = newStr[arr.join('').indexOf(maxNum)];
  return {'maxABC': maxABC, 'maxNum': maxNum};
};

var result = getMax(str);
console.log('出现最多的字符为：' + result.maxABC + ', 出现次数为： ' + result.maxNum);

```

网友方法：

```js

function simple(str){
  var obj = {};
  //遍历str拆解其中的每一个字符将其某个字符的值及出现的个数拿出来作为obj的kv
  for (var i = 0; i < str.length; i++) {
      if (!obj[str.charAt(i)]) {
          obj[str.charAt(i)] = 1;
      } else {
          obj[str.charAt(i)]++;
      }
  }
  var value = '';
  var num=0;
  for (var i in obj) {
      if (obj[i]>num) {
          num = obj[i];
          value = i;
      }
  }
  console.log('出现最多的值是'+value+'出现次数为'+num);
}

```

做个记录，没有对比就没有伤害，还是别人家的方法简单些。对字符串的一些方法还是不够熟练。还是要多用才能有更棒的方式方法来解决实际问题。