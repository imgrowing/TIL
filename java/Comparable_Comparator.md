# Comparable, Comparator

#### Comparable
- java.lang.Comparable

- 정의
    - 기본 정렬 기준이 되는 메서드를 정의하는 Interface
    - Integer, Double: 오름차순 정렬
    - String: 사전순 정렬

- 구현
    - compareTo() 구현
    - 현재 객체 < 파라미터로 넘어온 객체: 음수 리턴
    - 현재 객체 == 파라미터로 넘어온 객체: 0 리턴
    - 현재 객체 > 파라미터로 넘어온 객체: 양수 리턴
    - 음수 또는 0이면 객체의 자리가 그대로 유지되며, 양수인 경우에는 두 객체의 자리가 바뀐다.


#### Comparator
- java.util.Comparator

- 정의
    - 기본 정렬 기준 외 다른 기준으로 정렬할때 사용하는 Interace
    - 오름차순 정렬을 내림차순으로 정렬할때 많이 사용한다.

- 구현
    - compare() 구현
    - 첫 번째 파라미터로 넘어온 객체 < 두 번째 파라미터로 넘어온 객체: 음수 리턴
    - 첫 번째 파라미터로 넘어온 객체 == 두 번째 파라미터로 넘어온 객체: 0 리턴
    - 첫 번째 파라미터로 넘어온 객체 > 두 번째 파라미터로 넘어온 객체: 양수 리턴
    - 음수 또는 0이면 객체의 자리가 그대로 유지되며, 양수인 경우에는 두 객체의 자리가 변경된다.
    - 즉, Integer.compare(x, y)(오름차순 정렬)와 동일한 개념이다.
    - return (x < y) ? -1 : ((x == y) ? 0 : 1);
    - 내림차순 정렬의 경우 두 파라미터의 위치를 바꿔준다.
    - Integer.compare(y, x)(내림차순 정렬)