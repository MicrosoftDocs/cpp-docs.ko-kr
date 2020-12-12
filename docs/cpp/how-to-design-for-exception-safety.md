---
description: '자세히 알아보기: 방법: 예외 안전성을 위한 디자인'
title: '방법: 예외 안전성을 위한 디자인'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
ms.openlocfilehash: a4b957803d822b495ae6d44bb6640dcbb4535397
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268641"
---
# <a name="how-to-design-for-exception-safety"></a>방법: 예외 안전성을 위한 디자인

예외에 대한 데이터와 함께 예외 메커니즘의 장점 중 하나는, 예외를 throw하는 문에서 이를 처리하는 첫 번째 catch 문으로 직접 이동할 수 있다는 점입니다. 처리기는 호출 스택에서 아무 상위 수준에나 있을 수 있습니다. try 문과 throw 문 사이에 호출되는 함수는 throw된 예외에 대한 정보를 알아야 할 필요가 없습니다.  하지만 예외가 위쪽으로 전파될 수 있는 어느 지점에서든 "예기치 않게" 범위 밖으로 이동할 수 있고, 부분적으로 생성된 개체, 누출된 메모리 또는 불안정한 상태의 데이터 구조를 벗어나지 않고도 그렇게 할 수 있도록 설계되어야 합니다.

## <a name="basic-techniques"></a>기본 기술

강력한 예외 처리 정책을 위해서는 신중한 계획이 필요하며 디자인 프로세스의 일부에 포함되어야 합니다. 일반적으로 대부분의 예외는 소프트웨어 모듈의 하위 계층에서 검색되고 throw됩니다. 하지만 일반적으로 이러한 계층은 오류를 처리하거나 최종 사용자에게 메시지를 제공하기에 충분한 컨텍스트를 갖지 못합니다. 중간 계층에서 함수는 예외 개체를 검사할 때 예외를 catch하고 다시 throw할 수 있거나, 궁극적으로 예외를 catch하는 상위 계층에 대해 제공할 추가적인 유용한 정보를 포함합니다. 함수는 예외를 완전히 복구할 수 없는 경우에만 예외를 catch하고 "무시"해야 합니다. 대부분의 경우, 중간 계층에서 올바른 동작은 예외가 호출 스택으로 전파되도록 하는 것입니다. 최상의 계층의 경우에서도 정확성을 보장할 수 없는 상태로 예외가 프로그램을 벗어나는 경우 처리되지 않은 예외로 인해 프로그램이 종료되도록 두는 것이 적합할 수 있습니다.

함수가 예외를 어떻게 처리하든 간에, "예외에 대한 안전성"을 보장하기 위해서는 다음과 같은 기본 규칙에 따라 설계해야 합니다.

### <a name="keep-resource-classes-simple"></a>리소스 클래스를 간단 하 게 유지

클래스에서 수동 리소스 관리를 캡슐화 하는 경우 단일 리소스 관리를 제외 하 고 아무 작업도 수행 하지 않는 클래스를 사용 합니다. 클래스를 간단 하 게 유지 하면 리소스 누수의 위험을 줄일 수 있습니다. 가능 하면 다음 예제와 같이 [스마트 포인터](smart-pointers-modern-cpp.md) 를 사용 합니다. 이 예제는 의도적으로 만들어졌으며, `shared_ptr`이 사용될 때의 차이점을 보여주기 위해 단순화한 것입니다.

```cpp
// old-style new/delete version
class NDResourceClass {
private:
    int*   m_p;
    float* m_q;
public:
    NDResourceClass() : m_p(0), m_q(0) {
        m_p = new int;
        m_q = new float;
    }

    ~NDResourceClass() {
        delete m_p;
        delete m_q;
    }
    // Potential leak! When a constructor emits an exception,
    // the destructor will not be invoked.
};

// shared_ptr version
#include <memory>

using namespace std;

class SPResourceClass {
private:
    shared_ptr<int> m_p;
    shared_ptr<float> m_q;
public:
    SPResourceClass() : m_p(new int), m_q(new float) { }
    // Implicitly defined dtor is OK for these members,
    // shared_ptr will clean up and avoid leaks regardless.
};

// A more powerful case for shared_ptr

class Shape {
    // ...
};

class Circle : public Shape {
    // ...
};

class Triangle : public Shape {
    // ...
};

class SPShapeResourceClass {
private:
    shared_ptr<Shape> m_p;
    shared_ptr<Shape> m_q;
public:
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }
};
```

### <a name="use-the-raii-idiom-to-manage-resources"></a>RAII를 사용 하 여 리소스 관리

예외를 안전 하 게 하려면 함수는 또는를 사용 하 여 할당 한 개체가 제거 되었는지 확인 하 `malloc` **`new`** 고, 예외가 throw 되더라도 파일 핸들과 같은 모든 리소스를 닫거나 해제 해야 합니다. RAII ( *리소스 획득 시 초기화* )는 이러한 리소스의 관리를 자동 변수의 수명에 연결 합니다. 정상적인 반환 또는 예외로 인해 함수가 범위를 벗어나면 모든 완전히 생성된 자동 변수에 대한 소멸자가 호출됩니다. 스마트 포인터와 같은 RAII 래퍼 개체는 해당 소멸자에서 적합한 delete 또는 close 함수를 호출합니다. 예외로부터 안전한 코드에서는 각 리소스의 소유권을 특정 종류의 RAII 개체로 즉시 전달하는 것이 매우 중요합니다. `vector`,, `string` `make_shared` , `fstream` 및 유사한 클래스는 리소스의 획득을 처리 합니다.  그러나 `unique_ptr` `shared_ptr` 리소스 취득은 개체 대신 사용자에 의해 수행 되므로 기존 생성은 특수 합니다. 따라서 *리소스 릴리스가 소멸* 되지만 RAII로 인 한 것은 아닙니다.

## <a name="the-three-exception-guarantees"></a>세 가지 예외 보장

일반적으로 예외 보안은 함수에서 제공할 수 있는 세 가지 예외 보증 ( *실패 없음 보장*, *강력한 보증* 및 *기본 보증*)을 기준으로 설명 됩니다.

### <a name="no-fail-guarantee"></a>실패 보장 안 함

오류 없음(?또는 "throw 없음") 보증은 함수가 제공할 수 있는 가장 강력한 보증입니다. 이 형태의 보증에서 함수는 예외를 throw하지 않거나 예외가 전파되는 것을 허용하지 않습니다. 하지만 (a) 이 함수가 호출하는 모든 함수도 오류 없음 보장을 제공하는지 알고 있고, (b) throw되는 모든 예외가 이 함수에 도달하기 전에 catch된다는 것을 알고 있고, (c) 이 함수에 도달할 수 있는 모든 예외를 catch하고 올바르게 처리하는 방법을 알고 있는 경우를 제외하고는 그러한 보증을 안정적으로 제공할 수 없을 것입니다.

강력한 보증 및 기본 보증은 소멸자에 대한 오류가 없다는 가정에 의존합니다. 표준 라이브러리의 모든 컨테이너 및 형식은 소멸자가 예외를 throw하지 않음을 보증합니다. 또한 반대되는 요구 사항도 있습니다. 표준 라이브러리의 경우 템플릿 인수와 같이 여기에 제공되는 사용자 정의된 형식은 예외를 throw하지 않는 소멸자를 포함해야 합니다.

### <a name="strong-guarantee"></a>강력한 보장

강력한 보증에서는 함수가 예외로 인해 범위를 벗어날 경우 메모리를 누출하지 않고 프로그램 상태가 수정되지 않아야 합니다. 강력한 보증을 제공하는 함수는 기본적으로 커밋 또는 롤백 의미를 갖는 트랜잭션입니다. 즉, 완전히 성공하거나, 아예 아무런 영향도 주지 않습니다.

### <a name="basic-guarantee"></a>기본 보증

기본 보증은 세 가지 중에서 가장 약한 보증입니다. 하지만 메모리 소비 또는 성능 면에서 강력한 보증에 대한 비용이 너무 높을 경우에는 최상의 선택일 수 있습니다. 기본 보증에서는 예외가 발생할 경우 메모리가 누출되지 않고 개체가 사용 가능한 상태로 유지되어야 합니다(데이터가 수정될 수 있다 하더라도).

## <a name="exception-safe-classes"></a>예외 안전 클래스

클래스는 그 자체가 부분적으로 생성되거나 부분적으로 제거되는 것을 방지함으로써 안전하지 않은 함수에 사용되는 경우에도 자체적으로 고유한 예외 안전성을 보장할 수 있습니다. 클래스 생성자가 완료 전에 종료되는 경우, 개체가 생성되지 않고 해당 소멸자가 호출되지 않습니다. 예외 전에 초기화된 자동 변수에는 해당 소멸자가 호출되겠지만, 스마트 포인터 또는 비슷한 자동 변수에 의해 관리되지 않는 동적으로 할당되는 메모리 또는 리소스는 누출됩니다.

기본 제공 형식은 모두 오류 없음을 보증하며, 표준 라이브러리 형식에서는 최소한 기본 보증이 지원됩니다. 예외로부터 안전해야 하는 모든 사용자 정의 형식에 대해서는 다음과 같은 지침을 따르십시오.

- 스마트 포인터 또는 다른 RAII 형식의 래퍼를 사용해서 모든 리소스를 관리합니다. 생성자가 예외를 throw하면 소멸자가 호출되지 않으므로 클래스 소멸자에서 리소스 관리 기능을 사용하지 않도록 합니다. 하지만 클래스가 리소스를 하나만 제어하는 전용 리소스 관리자인 경우에는 리소스 관리를 위해 소멸자를 사용할 수 있습니다.

- 기본 클래스 생성자에서 throw된 예외는 파생된 클래스 생성자에서 무시될 수 없습니다. 파생된 생성자에서 기본 클래스 예외를 변환하고 다시 throw하도록 하려면 함수 try 블록을 사용하십시오.

- 특히 클래스에 "실패 허용 초기화" 개념이 사용된 경우에는 스마트 포인터에서 래핑된 데이터 멤버에 모든 클래스 상태를 저장할지 여부를 고려합니다. C++에서는 초기화되지 않은 데이터 멤버가 허용되지만, 초기화되지 않았거나 부분적으로 초기화된 클래스 인스턴스가 지원되지 않습니다. 생성자는 성공 또는 실패해야 합니다. 생성자가 완료 시점까지 실행되지 않으면 개체가 생성되지 않습니다.

- 예외가 소멸자로부터 벗어나도록 허용하지 않습니다. C++의 기본 원리에서는 소멸자가 호출 스택으로 예외를 전파하도록 허용해서는 안됩니다. 소멸자가 잠재적 예외를 throw할 수 있는 작업을 수행해야 하는 경우에는 try catch 블록에서 작업을 수행하고 예외를 무시해야 합니다. 표준 라이브러리에는 여기에서 정의하는 모든 소멸자에 대해 이 수준의 보증을 제공합니다.

## <a name="see-also"></a>참고 항목

[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](errors-and-exception-handling-modern-cpp.md)<br/>
[방법: 예외 코드와 비 예외 코드 간 인터페이스](how-to-interface-between-exceptional-and-non-exceptional-code.md)
