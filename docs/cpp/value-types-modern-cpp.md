---
description: '자세한 정보: c + + 클래스 값 형식'
title: 값 형식으로서의 C++ 클래스
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: cba028f73ef55be76dd7d405a25fd423f3897af4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116681"
---
# <a name="c-classes-as-value-types"></a>값 형식으로서의 C++ 클래스

C + + 클래스는 기본적으로 값 형식입니다. 이러한 개체를 참조 형식으로 지정할 수 있으며,이를 통해 다형성 동작이 개체 지향 프로그래밍을 지원할 수 있습니다. 값 형식은 종종 메모리와 레이아웃 컨트롤의 관점에서 볼 수 있는 반면 참조 형식은 다형성을 위한 기본 클래스 및 가상 함수에 대 한 것입니다. 기본적으로 값 형식은 복사 가능 합니다. 즉, 항상 복사 생성자와 복사 할당 연산자가 있습니다. 참조 형식의 경우 클래스를 복사할 수 없도록 설정 하 고 (복사 생성자 및 복사 할당 연산자 사용 안 함) 의도 된 다형성을 지 원하는 가상 소멸자를 사용 합니다. 값 형식은 내용에 대 한 정보도 있습니다. 복사 된 경우에는 별도로 수정할 수 있는 독립적인 두 값을 항상 제공 합니다. 참조 형식은 id에 대 한 것입니다. 개체 종류는 무엇 인가요? 따라서 "참조 형식"을 "다형 형식"이 라고도 합니다.

참조와 비슷한 형식 (기본 클래스, 가상 함수)을 원하는 경우 다음 코드의 클래스에 표시 된 것 처럼 명시적으로 복사를 사용 하지 않도록 설정 해야 `MyRefType` 합니다.

```cpp
// cl /EHsc /nologo /W4

class MyRefType {
private:
    MyRefType & operator=(const MyRefType &);
    MyRefType(const MyRefType &);
public:
    MyRefType () {}
};

int main()
{
    MyRefType Data1, Data2;
    // ...
    Data1 = Data2;
}
```

위의 코드를 컴파일하면 다음과 같은 오류가 발생 합니다.

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>값 형식 및 이동 효율성

새 복사 최적화로 인해 복사 할당 오버 헤드가 방지 됩니다. 예를 들어 문자열 벡터 중간에 문자열을 삽입 하는 경우에는 복사 재할당 오버 헤드가 발생 하지 않으며,이로 인해 벡터 자체가 증가 하는 경우에도 이동이 발생 합니다. 이는 두 개의 매우 큰 개체에 대 한 추가 작업을 수행 하는 경우와 같은 다른 작업에도 적용 됩니다. 이러한 값 작업 최적화를 사용 하도록 설정 하려면 어떻게 해야 하나요? 일부 c + + 컴파일러에서는 컴파일러에 의해 복사 생성자가 자동으로 생성 될 수 있는 것 처럼 컴파일러에서이를 암시적으로 사용 하도록 설정 합니다. 그러나 c + +에서는 클래스 정의에서 선언 하 여 클래스에서 할당 및 생성자를 이동 하기 위해 "옵트인 (opt in)" 해야 합니다. 이는 적절 한 멤버 함수 선언에서 이중 앰퍼샌드 (&&) rvalue 참조를 사용 하 고 이동 생성자 및 이동 할당 메서드를 정의 하 여 수행 됩니다.  또한 소스 개체에서 "중요"를 "도용" 하는 올바른 코드를 삽입 해야 합니다.

이동을 사용 하도록 설정 해야 하는지 여부를 결정 하려면 어떻게 해야 하나요? 복사 생성을 사용 하도록 설정 해야 하는 경우에는 전체 복사 보다 비용이 적게 들 수 있는 경우 이동을 사용 하도록 설정 하는 것이 좋습니다. 그러나 이동 지원이 필요한 경우에는 복사를 사용 하도록 설정 하는 것이 반드시 필요한 것은 아닙니다. 이 후자의 경우를 "이동 전용 형식" 이라고 합니다. 표준 라이브러리에 이미 있는 예제는 `unique_ptr` 입니다. 참고로, 이전 `auto_ptr` 버전은 더 이상 사용 되지 않으며 `unique_ptr` 이전 버전의 c + +에서 이동 의미 체계 지원이 부족 하기 때문에 정확 하 게 대체 되었습니다.

이동 의미 체계를 사용 하 여 값으로 반환 하거나 중간에 삽입할 수 있습니다. 이동은 복사의 최적화입니다. 해결 방법으로 힙 할당이 필요 합니다. 다음 의사 코드를 살펴보겠습니다.

```cpp
#include <set>
#include <vector>
#include <string>
using namespace std;

//...
set<widget> LoadHugeData() {
    set<widget> ret;
    // ... load data from disk and populate ret
    return ret;
}
//...
widgets = LoadHugeData();   // efficient, no deep copy

vector<string> v = IfIHadAMillionStrings();
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)
//...
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);
//...
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies
```

### <a name="enabling-move-for-appropriate-value-types"></a>적절 한 값 형식에 대 한 이동 사용

이동이 전체 복사본 보다 저렴 한 값과 유사한 클래스의 경우 효율성을 위해 이동 생성 및 이동 할당을 사용 하도록 설정 합니다. 다음 의사 코드를 살펴보겠습니다.

```cpp
#include <memory>
#include <stdexcept>
using namespace std;
// ...
class my_class {
    unique_ptr<BigHugeData> data;
public:
    my_class( my_class&& other )   // move construction
        : data( move( other.data ) ) { }
    my_class& operator=( my_class&& other )   // move assignment
    { data = move( other.data ); return *this; }
    // ...
    void method() {   // check (if appropriate)
        if( !data )
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");
    }
};
```

복사 생성/할당을 사용 하는 경우 전체 복사본 보다 비용이 적게 들 수 있는 경우에도 이동 생성/할당을 사용 하도록 설정 합니다.

일부 *비 값* 유형은 이동 전용입니다. 예를 들어 리소스를 복제할 수 없는 경우에만 소유권을 전송할 수 있습니다. 예: `unique_ptr`.

## <a name="see-also"></a>참고 항목

[C + + 형식 시스템](../cpp/cpp-type-system-modern-cpp.md)<br/>
[C++ 시작하기](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)
