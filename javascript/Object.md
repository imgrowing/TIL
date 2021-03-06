# Object
- Object 객체의 생성자는 window객체에 저장되어있다.
- 모든 객체가 Object 객체로부터 상속받기 때문에 모든 객체는 Object객체의 메서드들을 사용할 수 있다.


# Method 

1. 객체.hasOwnProperty(속성명);
- 객체의 속성이 상속받지 않은 속성인지 알려준다.
자신의 속성 : true
부모의속성 or 속성이아닐경우 : false 


2. 객체.isPrototypeOf(대상);
- 객체가 대상의 조상인지 알려준다. 

3. Object.getPrototypeOf(객체) , Object.setPrototypeOf(객체,prototype)
- 객체의 prototype을 조회하거나 설정할 수 있다.

4. instance of 
- child instanceof Parent;
- 객체 가 특정 생성자의 자식인지 조회할수 있다

5. 객체.propertyIsEnumerable(속성)
- 해당 속성이열거가능한 속성인지 알려준다. (반복문으로 열거가 가능한지 여부)
- 상속받은 속성과 해당 객체의 속성이 아닌것은 제외된다.

6. 객체.toString
- 객체를 로깅하는중 [object Object] 라고 나올경우가 있다.
이경우에 내부적으로 toString메서드가 호출된 결과이다. 문자열끼리 더할때 주로호출되며 
기본적으로는 객체의종류를 알려준다.

7. 객체.valueOf
- 객체의 기본값을 의미한다. 
숫자 계산시 내부적으로 호출된다.

8. Object.create(prototype,속성)
```javascript
var obj = {}; // Object.create(Object.prototype); 과 같다.
var obj2 = Object.crate(null,{
    a: {
        writable: true,
        configurable: false,
        value: 5,
    }
});
```
- 객체를 생성하는 방법중 하나이며 속성들은 writable,configurable,enumerable,get,set,value 의 옵션이있다.

9. Object.definedProperties(객체,속성들), Object.definedProperty(객체,속성,설명)
- 객체의 속성을 상세히 정의할수있다. 
writable : 변경가능유무
enumerable : 열거 가능유무 (for..in 반복문내 사용유무)
configurable : 속성의 설명 변경 가능유무 
value : 속성의 값
get : value를 get 
set : value를 set
```javascript
var obj = {};
Object.defineProperties(obj, {
  a: {
    value: 5,
    writable: false,
    enumerable: true,
  },
  b: {
    get: function() {
      return 'name';
    },
    set: function(value) {
      console.log(this, value);
      this.a = value;
    },
    enumerable: false,
    configurable: false,
  },
});
obj.a; // 5
obj.b; // 'name'
obj.a = 10;
obj.a; // writable이 false라 그대로 5
for (var key in obj) {
  console.log(key); // b의 enumerable이 false이니까 a만 log됨
}
obj.b = 15; // 15로 설정되는 대신 set의 내용이 실행됨. set의 value는 15
obj.a; // this.a = value로 인해 15로 바뀌어야 하나 writable이 false라 무시됨
obj.b; // 그대로 'name'
Object.defineProperty(obj, 'b', {
  value: 5
}); // Uncaught TypeError: Cannot redefine property: b
```

10. Object.getOwnPropertyDescriptor(객체,속성);

Object.getOwnPropertyDescriptor(obj,'b');
- 속성의 설명값을 불러온다.


11. Object.freeze, Object.seal, Object.preventExtensions 

var obj2 = Object.freeze(obj);

Object.freeze : 값 변경 불가 , 속성 추가 및 제거 불가 속성 설명도 바꿀 수 없다.
Object.seal : 숙성 추가 및 제거 불가 , configurable을 false로 변경 , writable : true 시 속성값 변경 가능 
Object.preventExtensions : 속성 추가 불가 , 그외 설정 가능 


12. Object.keys

- 객체의 속성명을 모두 가져와 배열로 생성한다. enumerable false 속성 제외 


13. Object.isFrozen, Object.isSealed, Object.isExtensible 
- 객체가 freeze , sealed , preventExtension 상태인지 알려준다.

14. typeof 
```javascript
var a = 1;
typeof a; // number
```
- 배열과 null도 object로 표현된다. 
배열구분시 Array.isArray , null 구분시 따로 처리해야한다.

15. delete 
```javascript
var obj = {a:'test'};
delete obj.a;
```
- 객체 내 속성을 제거한다. 성공여부 boolean값 반환 
