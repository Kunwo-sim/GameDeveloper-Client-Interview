## C++ cast

캐스팅은 일단 명시적 캐스팅, 묵시적 캐스팅으로 나뉘게 됩니다.

묵시적 캐스팅의 경우에는 다른 표기 없이 호환되는 타입들로 변환할 수 있게 해주지만 데이터 손실이 발생할 수도 있고 유지보수 측면에서도 알아내기 어려우므로 가급적 사용하지 않는게 좋습니다.



C 스타일의 명시적 캐스팅은 아래와 같습니다.

```c++
float f = 1.1f;
int a = (int)f;
```

다만 이 경우 코드 분간이 어렵기도 하고 C의 유산이므로 C++의 여러 캐스팅 연산자들을 사용하게 됩니다.



### static_cast

기존 C스타일의 형변환 대신 사용하게 됩니다. 형변환이 가능한지에 대한 검사는 컴파일 타임에 하게 됩니다.

```c++
float f = 1.1f;
int a = static_cast<int>(f);
```



### const_cast

이는 const를 제거, 부여하는데 사용이 됩니다. 다만 부여의 경우에는 사용하는 경우가 잘 없게 됩니다.

```c++
void NonConstFunc(Some s);

//...
const Some s;
NonConstFunc(s);   // ERROR!
NonConstFunc(const_cast<Some>(s))
```



### reinterpret_cast

모든 포인터 유형을 다른 포인터 방식으로 변경할 수 있게 됩니다. 또한 포인터 타입을 정수로 바꾸는데도 가능한 캐스팅입니다.

이런 식으로 강력한 형변환을 하기 때문에 자주 사용하지 않게 되며 메모리 단위로 분해, 재조립을 하는 캐스팅이므로 이해도가 필요한 캐스팅입니다.



### dynamic_cast

클래스의 포인터나 참조에만 사용할 수 있으며 런타임에 캐스팅을 진행하게 됩니다. RTTI(Runtime Type Information)를 위한 캐스팅이라 할 수 있습니다. 다만 클래스간 virtual 함수가 있어야 하며 만일 다형성이 없는 객체들 간 캐스팅에서는 컴파일 에러가 나오게 됩니다,