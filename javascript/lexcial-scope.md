# 렉시컬 스코프 (Lexical Scope)

- 스코프는 함수를 호출할 때가 아닌 '선언' 할때 생긴다.
정적 스코프라고도 불린다.
```javascript
var name = 'myName';
function logForName(){
    console.log(name);
}

function test(){
    var name= 'test';
    logForName();
}

test(); // myName 
```
* 네임스페이스 
```javascript
var obj = {
    x : 'local',
    y : function (){
        alert(this.x);
    }
}
obj.x;
obj.y();
```
- 위와같은 경우엔 obj.x obj.y()와 같이 접근해야하기때문에 다른사람들과 변수가 겹치는 일이 없다.
이러한 방법을 네임스페이스를 만든다고표현한다.
