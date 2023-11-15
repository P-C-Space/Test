## Iterator


### Iterator(interface) -(extends)-> InfiniteIterator(interface) 의 의견 ( 2023. 11. 13 )
 * InfiniteIterator 는 Iterator 를 상속받아야하는가?
 * InfiniteIterator 무한히 작동하는 코드와 Iterator는 다른 것이 아닌가?
   * 받아야 한다. 명시적으로 InfiniteIterator라는 interface를 선언한 것일 뿐 기능은 Iterator 의 hasNext를 ture로 만든 것이다.
 * LSP 원칙을 위배하는가?
   * 위배하지 않는다. Iterator를 사용하는 메서드가 Iterators에 존재하지만 InfiniteIterator를 사용하기 위해서는 난해한 메서드(Precondition or Exception 처리 필요)들이 존재 한다.
 
 * 만약 위에서 언급했듯이 새로운 Iterator 선언할 때 hasNext를 true를 준 Iterator를 생성한다면 그건 Iterator가 아니게 되는가?
   * 그것 또한 Iterator이다 그러므로 나는 hasNext와 next를 사용하는 InfiniteIterator는 Iterator를 상속받아야 한다고 생각한다.

 * LSP 원칙은 무엇인가?
   * 서브타입은 기반타입으로 대체될 수 있어야함.
   * 다형성을 지원하기 위한 원칙

 * 자바는 InfiniteIterator 역할을 하는 Stream과 Iterator를 분리하였는가?
   * 내부반복자 외부반복자
     * 내부 반복자
       * 컬렉션 내부에서 요소들을 반복 시키고, 개발자는 요소하나당 처리해야 할 코드만 제공하는 코드 패턴
     * 외부 반복자
       * 외부적으로 반복을 명시 개발자가 코드를 작성해 직접 가져오는 방식으로 for문, while문이 대표적
