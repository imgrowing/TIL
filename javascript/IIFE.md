# IIFE (즉시실행함수 패턴 , 모듈패턴)

- 함수를 선언과 동시에 바로 실행시켜버리는것.
비공개 변수가 없는 자바스크립트에 비공개 변수 기능을 만들어준다.
```javascript
var iife = (function(){
    var x = 'local';
    return {
        y: function(){
            alert(x);
        }
    };
})();
iife.y(); 

```
