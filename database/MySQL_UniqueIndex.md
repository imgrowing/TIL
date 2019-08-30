# MySQL Index, Unique Index

#### UniqueIndex
- 컬럼값에 중복값이 존재하지 않도록 하는 인덱스(단, Primary key가 아닌 유니크 인덱스는 NULL 값을 여러개 가질 수 있음)
- Unique 는 사실 제약 조건에 가깝다.
- 해당 컬럼의 유일성만을 보장하는 것을 원할뿐 인덱스는 아니다.
- MySQL 에서는 인덱스없이 Unique 제약을 설정할 방법이 없다.

#### Index Scan
- 많은 사람들이 유니크 인덱스가 빠르다고 생각하지만 사실이 아니다.
- 유니크 인덱스는 값이 유일하므로 값을 1개만 읽어들이면 되고, 인덱스는 여러개 읽어들여야 하는 것이 사실이지만
- 사실상 인덱스가 한번 읽어들여져서 하나하나 값을 비교하는 단계에서는 이미 CPU가 그 처리를 담당하고 있다.
- 인덱스는 중복이 허용되어 처음 LOAD 시 양이 많아서 느릴뿐 속성 자체에 의한 딜레이는 아니다.

* UniqueIndex 와 Index의 읽기 성능은 거의 차이가없다.

#### Index Write
- Unique Index가 적용된 컬럼에 새로운 값이 Insert될때는 중복을 체크해야하는 과정이 더 필요하기때문에 일반 Index보다 느리다.
- 여기서 중요한 점은 MySQL 이 중복 체크시 읽기잠금, 쓰기시 쓰기 잠금을 사용하기 때문에 이 과정에서 데드락이 아주 빈번하게 발생한다.

InnoDB 사용시 Index 키의 저장을 버퍼링 할 수 있으나, UniqueIndex 의 경우에는 중복 체크로 인해 버퍼링이 불가능 하다.

* UniqueIndex 는 중복 체크 과정 때문에 일반 Index보다 쓰기 성능이 더 느리다.


#### 주의사항
- 유일성을 보장해야하는 데이터라면 UniqueIndex를 생성하는것이 맞다.
- 하지만 성능을 목적으로 불필요한 UniqueIndex 생성은 하지말것.
- 어떤 컬럼에 UniqueIndex가 존재하는 경우 해당컬럼과 비슷한 성질의 다른 컬럼에 보조인덱스를 만들 필요는 없다.