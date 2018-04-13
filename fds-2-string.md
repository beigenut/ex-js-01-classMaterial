### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```


```
function insensitiveEqual(x, y){
  str1 = x.toLowerCase();
  str2 = y.toLowerCase();
  if(str1 === str2){
    return true;
  }else{
    return false;
  }
}
```





### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```



## 1번 풀이 ##

```
leftPad = (s,n) => {
  len = s.length
  if(len < n){
    return ' '.repeat(n - len) + s;
  }
  else{
    return s;
  }
}
```


## 2번 풀이 ##

```
'efdr'.padStart(10);
```



## (응용) 원하는 숫자만큼 앞에 공백넣기 ##

```
function pad(str, num){
  padNum = num+str.length;
  console.log(str.toString().padStart(padNum));
}
```







### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.


## 1번 풀이 ##

```
function cntVowel(str){
  let cnt = 0;
  for(let i = 0; i<str.length; i++){
    if(str[i].includes('a') || str[i].includes('e') || str[i].includes('i') || str[i].includes('o') || str[i].includes('u')){ 
      cnt++;
    }
    
  }return cnt;
}
```

## 2번 풀이 ##

```
function cntVowel(str){
  let cnt = 0;
  for(let i = 0; i<str.length; i++){
    if(str[i].includes('a')){
      cnt++;
    }if(str[i].includes('i')){
      cnt++;
    }if(str[i].includes('e')){
      cnt++
    }if(str[i].includes('u')){
      cnt++;
    }if(str[i].includes('o')){
      cnt++;
    }
  }return cnt;
}
```





____

### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```


```
function cntChar(str){
  const obj = {};
  for(let i=0; i<str.length; i++){
    const char = str[i];
    // 만약 속성이 없다면
    if(obj[char] == null){
      // 속성값에 1 저장
      obj[char] = 1;
    }else{
      // 속성값이 이미 있다면 1 증가
      obj[char]++;
    }
  }return obj;
}
```

_____








### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)



## 1번 풀이 ##

```
function palindrome(str){    
    for(let i = 0; i<Math.floor(str.length/2); i++){
      if(str[i] !== str[str.length-1-i]){
        return false;   
    }
  }return true;
}
```

## 2번 풀이 ##

```
function isPalidrome(str){
  return [...str].reverse().join('') === str;
}
```






### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```

```
function sliceLetter(str){
  const arr=[];
  for(let i=0; i<str.length; i++){
    for(let j=i+1; j<=str.length; j++){
      console.log(i, j);
      arr.push(str.slice(i, j));
    }
  }return arr;
}
```

> 3중 for 문은 해당 문제 풀이에 해당없음.







### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```


```
function removeDup(str){
  let newStr = '';
  for(let i=0; i<str.length; i++){
      if(!newStr.includes(str[i])){
        newStr += str[i];
      }
  }return newStr;
}
removeDup('tomato');
```


> replace() 을 쓰는 방법도 있을 것 같은데, 배열1의 배열2와 중복된 문자열을 `replace(arr2,'')` 으로 리플레이스 제거도 가능한지 모르겠다.







### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.
- `split` 메소드를 이용해서 풀어보세요.


## 풀이 1번 ##

```
function replaceStar(str){
  let cnt = 0;
  const arr = [...str];
  for(let i=0; i<str.length; i++){
    cnt ++;                               // atPos = i 와 같음.
    if(arr[i] === '@'){
      break;
    }
  }
  const after = str.slice(cnt-1, str.length);
  console.log(cnt);
  return '*'.repeat(cnt-1) + after;
}
```



## 풀이 2번 ##

```
function replaceStar(str){
  const arr = str.split('@');
  console.log(arr);
  const stars = '*'.repeat(arr[0].length);
  const domain = arr[1];
  return stars + '@' + domain;
}
```

> split 함수를 이용해서 원하는 스트링을 기준으로 2개의 배열로 나눌 수 있음.






### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.


```
function letterCaseTranslate(str){
  let newStr = '';
  for(let i=0; i<str.length; i++){
    if(str[i] === str[i].toLowerCase()){
      newStr += str[i].toUpperCase();
    }else{
      newStr += str[i].toLowerCase();
    }
  }return newStr;
}
```






___ 

### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)


```
function myFunction(str){
  const arr = str.split(' ');
  for(let i=0; i<arr.length; i++){
    arr[i] = arr[i].replace(arr[i].charAt(0), arr[i].charAt(0).toUpperCase());
    console.log(arr[i].charAt(0));
    console.log(arr);
  }
  return arr.join(' ');
}
```

> 문자열을 '(space)' 를 기준으로 짤라 `.split` 배열(const arr)에 저장. 각 배열 첫 번째 문자를 `.charAt(n)` 으로 찝고 이를 `.toUpperCase()` 로 변환시킨 것으로 강제 `.replace()` 한다. 

___





### 문제 11

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)


## 1번 풀이 ##

```
function maxLength(str){
  let currentLen = 0;
  let maxLen = 0;
  for(let i=1; i<str.length-1; i++){
    if(str[i] !== ' '){
      currentLen ++;
    } else{
      if(maxLen < currentLen){
        maxLen = currentLen;
      }else{
        currentLen = 0;
      }
    }
  }return maxLen;
}
```

## 2번 풀이 ##

```
function maxLength(str){
  const arr = str.split(' ');
  let maxLen = 0;
  for(let i=0; i<arr.length; i++){
    maxLen = maxLen < arr[i].length ? arr[i].length : maxLen;
  }
  return maxLen;
}
```





### 문제 12

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.












### 문제 13

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.












### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.











### 문제 15


`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```














### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```














### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```
