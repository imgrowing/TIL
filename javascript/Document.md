# Document 


#### 선택자

- 1. document.getElementById('아이디');
    - 해당 아이디를가진 태그를 선택한다.

- 2. document.getElementsByClassName('클래스명');
    document.getElementsByName('이름');
    document.getElementsByTagName('태그');
    - 각각 해당 클래스,네임,태그명을 가진 태그들을 선택한다.
    - 항상 배열의 형태로 리턴된다. 

- 3. document.querySelector('선택자');
    document.querySelectorAll('선택자');
    - css 선택자로 선택이 가능하다.
    - 아이디는 # , 클래스는 . 태그명[속성=속성값] 도 가능하다 

#### 생성자

- 1. document.createElement(태그명);
- 새로운 태그를 만들때사용한다.
- 변수를 통해 메모리에 저장되며 appendChild 등 추가하는 메서드를사용하여 추가해야한다.

- 2. document.createTextNode(텍스트);
    - 텍스트를 생성한다. 변수를 통해 메모리에 저장된다.

- 3. document.createDocumentFragment();
```javascript
var div = document.createElement('div');
var text = document.createTextNode('텍스트');
var fragment = document.createDocumentFragment();
div.appendChild(text);
fragment.appendChild(div);
document.body.appendChild(fragment);
```

- dummy Document 를 생성한다. 
JS로 document를 조작하는것은 매우 성능이 떨어진다.
반복문을 사용하여 추가시에는 dummy Document를 생성하여 추가를 한후
한번에 document를 추가하게되면 실제 document조작은 한번만 일어나게되므로 성능 부담이 덜어진다.

#### 그외 

document.head head 에 접근
document.body body 에 접근
document.anchors 앵커에 접근
document.links 링크에 접근
document.forms 폼에 접근
document.images 이미지에 접근
document.scripts 스크립트에 접근
