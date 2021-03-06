# OOP (Object Oriented Programming)

1. 생성자 

- 객체를 생성하는 함수를 생성자 함수라고한다.
다른 언어에서는 class가 있지만 자바스크립트에서는 존재하지않아
생성자함수가 그 역할을 대신한다.
```javascript
function Person(name,age){
    this.name=name;
    this.age=age;
    this.hello=function(){
        alert(...);
    }
}
```
- 함수를 정의할때 function 키워드를 사용하지만 함수와는달리 대문자로 시작하게만든다.
생성자를 바탕으로 사람객체를 만들때 new 라는 키워드를 사용하여 호출한다.
```javascript
var one = new Person('myName',10);
```
new 를 통해 호출된 함수는 인스턴스화되며 이때의 this는 객체 자신을 가리키게된다. 



2. 프로토타입
```javascript
function Person(name,age){
    this.name = name;
    this.age = age;
}
Person.prototype.hello = function(){
    ....
}
```
- this.hello 로 메서드를 정의하지않고 
Person.prototype.hello = function(){} 으로 정의하였다.
prototype 객체는 같은 생성자로부터 만들어진 객체들은 모두 이 원형 객체를 공유하게된다.
Person의 prototype객체에 hello 메서드를 정의하면 Person 생성자로 생성된 모든 객체는 hello 메서드를 사용할수있다.
prototype 은 모든 객체가 공유하기때문에 최초 1회 생성되지만 , this에 넣은것들은 객체 생성시마다 생성되기때문에 메모리 낭비가 발생한다.
메서드뿐 아니라 속성도 prototype에 넣을수있다.



3. prototype과 __proto__ 

- new Person('myName',10); // Person {name:"myName",age:10,__proto__:Object}
__proto__ 가 실제 객체를 만들때 생성자의 prototype이 참조된것이다.
prototype을 참조하기때문에 __proto__ 와 prototype은 같다.




