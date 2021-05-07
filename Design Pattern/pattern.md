1. 목적 
- 소프트웨어 개발시에 반복적 혹은 고질적으로 발생하는 문제들이 거듭 발생하였을 때 사용할만한 해결책
- 직접적인 라이브러리, API와 같은 개념은 아님.
- 설계에 대한 기본적인 패턴.

2. SOLID(객체지향 설계 원칙)
- **S**ingle Responsibility Principle 
    - 모든 클래스는 각각 하나의 책미만 가져야 한다.
- **O**pen - Close Principle 
    - 개방-폐쇄 원칙
    - 확장에는 열려 있고, 수정에는 닫혀 있음.
    - 기존의 코드 수정을 하지 않음(close)
    - 기능을 추가할 수 있음(open)
- **L**iskov Substitution Principle
    - 자식 클래스는 언제나 자신의 부모 클래스를 대체할 수 있다는 원칙.
    - 부모 클래스가 들어갈 자리에 자식 클래스를 넣어도 잘 작동함.
    - 즉, 자식 클래스는 부모 클래스에 대한 확장만 수행하도록 해야함.
- **I**nterface Segregation Principle
    - 하나의 일반적인 인터페이스보다 여러개의 구체적인 인터페이스가 낫다. 
    - 인터페이스를 작은 단위로 구체적이게 분리시켜야 한다.
- **D**ependency Inversion Property
    - 상위 모듈이 하위 모듈에 의존하면 안됨.

3. 분류 
- 생성 패턴(Creational) : 객체의 생성 방식(인스턴스를 만드는 절차)
- 구조 패턴(Structural) : 객체간의 관계를 조직
    - 서로 독립적으로 개발한 인터페이스 혹은 객체를 묶어 단일의 것으로 만들 때 새로운 기능을 제공하는 패턴
- 행위 패턴(Behavioral) : 객체의 행위를 조직

4. 싱글턴 패턴(Singleton)
- 분류 : 생성 패턴
- 객체를 생성할 때, 전역변수를 사용치 않고, 객체를 **단 하나**만을 만들되, 어디에서든 참조할 수 있도록 생성하는 패턴
- 예시
```java
public class Screen{
    private static Screen screen = null;
    private Screen(){}
    // 생성자 접근을 제한함.
    // 단 하나의 객체 생성만을 허용함.
    public static Screen getScreen(){
        if(screnn == null) screen = new Screen();
        return screen;
    }
    public void render(Picture p){
        // rendering method
    }
}
```

5. 어댑터 패턴(Adapter)
- 분류 : 구조 패턴
- 클래스의 호환 혹은 함수명과 같은 문제로 바로 사용하거나 대체할 수 없는 경우가 있음.
- 만약 같은 역할을 하는 함수를 직접 매핑할 수 있다면, 사이의 변환 클래스를 둠으로써 클라이언트 그대로 활용 가능.
- Cat클래스를 인터페이스로 사용하며, 이를 사용하기 위한 Tiger클래스의 어댑터를 만듬. 이를 통해 Cat 클래스의 함수를 이용하여 같은 역할을 수행하는 Tiger 클래스를 이용할 수 있음.
```java
public interface Cat{
    public void crying();
    public void run();
}
public class Tiger  {
    public void growl(){
        System.out.println("어흥");
    }
    public void tiger_run(){
        System.out.println("호랑이의 뜀걸음");
    }
}
public class TigerAdapter implements Cat{
    Tiger tiger;
    public TigerAdapter(Tiger tiger){
        this.tiger = tiger;
    }
    @Override
    public void crying(){
        tiger.growl();
    }
    @Override
    public void run(){
        tiger.tiger_run();
    }
}
```

