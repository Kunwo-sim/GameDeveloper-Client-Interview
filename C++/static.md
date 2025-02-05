## static 멤버 변수

클래스의 static 멤버 변수는 **모든 클래스의 인스턴스들이 공유하는 멤버**로 프로그램의 수명 내 한번만 초기화되면서 계속해서 메모리에 올라가 있게 됩니다.

```c++
class Some
{
private:
    static int var;
    
    // Some()
    //     : var(1)
    // {}    -> 생성자 내에서도 초기화 불가능
    
}

int Some::var = 0;  // 전역 범위에서 초기화 가능합니다.
```

만일 헤더와 cpp 파일을 분리해서 개발하는 경우 반드시 cpp파일에서 초기화를 해줘야 합니다.

추가로 이 멤버의 접근 지정자가 private이라 하더라도 전역범위 초기화가 가능합니다.



다만 **static const 변수의 경우에는 클래스에서 초기화 하는 것이 가능**합니다. 이는 [const]()의 특성 상 값을 변경하는게 불가능하며 컴파일 타임 초기화가 되므로 가능합니다.



## static 멤버 함수

클래스 내 static 함수는 모든 클래스가 공유하는 함수로 객체와는 관계 없이 호출될 수 있습니다. 

이 함수 내에서는 일반 멤버 변수, 즉 `this`가 붙는 멤버에 대해서는 연산을 할 수 없습니다. 다만 static 멤버 변수, 함수에 대한 연산을 사용할 수 있습니다.