## Iterator
### Iterator(interface) -(extends)-> InfiniteIterator(interface) + Iterator(interface) -(extends)-> FiniteIterator(inteface) 의견 ( 2023. 11. 14 )
* 11.13의 의견을 토대로 그렇다면 반대인 무한한이 아닌, 유한한으로 FiniteIterator를 명시적으로 생성함으로써 Finite만 들어와야하는 메서드들에 매개변수 타입을 Iterator가 아닌 FiniteIterator로 조정하였다.
* 다음과 같은 효과로 InfiniteIterator가 매개변수 역할을 하면 발생하는 (무한루프같은) 오류를 FiniteIterator로 대체하면서 피할 수 있다.

### Iterator(interface) -(extends)-> InfiniteIterator(interface) 의 의견 ( 2023. 11. 13 )
 * InfiniteIterator 는 Iterator 를 상속받아야하는가?
 * InfiniteIterator 무한히 작동하는 코드와 Iterator는 다른 것이 아닌가?
   * 받아야 한다. 명시적으로 InfiniteIterator라는 interface를 선언한 것일 뿐 기능은 Iterator 의 hasNext를 ture로 만든 것이다.
 * LSP 원칙을 위배하는가?
   * 위배하지 않는다. Iterator를 사용하는 메서드가 Iterators에 존재하지만 InfiniteIterator를 사용하기 위해서는 난해한 메서드(Precondition or Exception 처리 필요)들이 존재 한다.
 
 * 만약 위에서 언급했듯이 새로운 Iterator 선언할 때 hasNext를 true를 준 Iterator를 생성한다면 그건 Iterator가 아니게 되는가?
   * 그것 또한 Iterator이다 그러므로 나는 hasNext와 next를 사용하는 InfiniteIterator는 Iterator를 extends하는 것은 문제가 없다고 생각한다.

 * LSP 원칙은 무엇인가?
   * 서브타입은 기반타입으로 대체될 수 있어야함.
   * 다형성을 지원하기 위한 원칙

 * 자바는 InfiniteIterator 역할을 하는 Stream과 Iterator를 분리하였는가?
   * 내부반복자 외부반복자
     * 내부 반복자
       * 컬렉션 내부에서 요소들을 반복 시키고, 개발자는 요소하나당 처리해야 할 코드만 제공하는 코드 패턴
     * 외부 반복자
       * 외부적으로 반복을 명시 개발자가 코드를 작성해 직접 가져오는 방식으로 for문, while문이 대표적
