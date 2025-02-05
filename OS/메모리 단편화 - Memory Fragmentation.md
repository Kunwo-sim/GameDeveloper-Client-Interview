## 메모리 단편화 - Memory Fragmentation



### 메모리 단편화란?

메모리 단편화는 **사용가능한 메모리는 충분히 있지만 이게 흩어져서 할당이 불가능한 경우**를 의미합니다. 종류는 **외부 단편화, 내부 단편화** 2가지가 있습니다.

- 내부 단편화
  - 할당시 프로세스가 필요한 메모리보다 많은 메모리를 할당한 경우를 의미합니다.
- 외부 단편화
  - 남은 전체 메모리는 충분히 있는데 이것들이 '연속된 공간'이 아니라 흩어져 있어 할당이 안되는 경우



### 메모리 단편화 해결법

> 외부 단편화 해결법

- 페이징
  - 페이징 기법은 보조 기억장치(디스크, SSD 등)를 메모리처럼 구역을 나눈 뒤 필요한 부분을 메모리로 옮겨서 사용하는 걸 의미합니다. 
  - 여기서 **Page, 페이지는 프로세스를 일정한 크기로 나눈걸 의미**합니다. 
  - 이 과정에서 첫 페이지를 우선 로드한 뒤 이후 페이지를 차례로 가져오는 방식입니다. 
  - 프로세스가 같은 페이지를 사용한다면 이를 함께 사용해 메모리를 절약할 수도 있고 이 페이지에 대한 테이블 (PTBR)이 필요하게 됩니다. 
  - 이로 인해 시간, 공간적 오버헤드가 나오게 되는데 시간적 오버헤드는 자주 사용하는 페이지 테이블을 저장하는 버퍼(TLB)를 둬서 해결을 할 수 있습니다.
- 압축
  - 비용이 많이 드는 작업입니다
  - 삭제 공간들을 회수해 메모리를 정리합니다.
- 통합
  - 압축과는 다르게 인접한 것들간의 메모리를 통합하는 작업입니다.



> 내부 단편화 해결

- 세그멘테이션
  - 페이징은 일정 크기로 나누는 것이고 세그멘테이션은 **논리 단위**를 의미합니다.
  - 이 논리 단위는 일정하지 않습니다.
  - 논리 주소와 실제 주소를 매핑하기 위한 테이블이 하나 필요하게 됩니다.
  - 세그멘테이션은 외부 단편화가 발생할 우려가 있고 단편화의 크기가 제멋대로라 페이징을 사용하게 됩니다.



> 둘 다 해결하는 방안

- 메모리 풀
  - 필요한 메모리를 직접 지정해 미리 할당받은 뒤 사용한 뒤 반납하는 기법입니다. 
  - 이런 풀링 없이 할당, 비할당을 계속하게 되면 단편화를 만들게 되지만 필요할 때마다 할당받은 메모리 공간을 가져다 쓰고 반납하기에 외부 단편화가 생기지 않게 됩니다. 
  - 또한 "필요한"만큼이라고 했기에 내부 단편화도 없게 됩니다.
  - 오브젝트 풀링과 비슷한 느낌이며 할당, 해제가 빈번한 경우 유용하게 사용할 수 있습니다.