---
title: C + + (최신 c + +)를 다시 시작 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb45f18c38323f8c5e56a7b9bd6148bb1ca6142
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070838"
---
# <a name="welcome-back-to-c-modern-c"></a>C++의 진화(최신 C++)

C++는 전세계적으로 가장 널리 사용되는 프로그래밍 언어 중 하나입니다. 잘 작성된 C++ 프로그램은 빠르고 효율적입니다. 이 언어는 재미있고 흥미로운 게임에서 고성능 과학 소프트웨어, 장치 드라이버, 포함 프로그램 및 Windows 클라이언트 응용 프로그램에 이르기까지 다양한 응용 프로그램을 만드는 데 사용할 수 있으며 유연성이 다른 언어보다 훨씬 더 뛰어납니다. C++는 20년 이상 이러한 문제와 기타 문제를 해결하는 데 사용되었습니다. 여러분은 모르겠지만, 오래된 C 스타일 프로그래밍을 접고 대신 최신 C++를 사용하는 C++ 프로그래머의 수가 점점 증가하고 있습니다.

C++의 본래 요구 사항 중 하나는 C 언어와의 역 호환성이었습니다. C++은 C with Classes, 원래 C++ 언어 사양, 많은 후속 기능 개선에 걸친 여러 번의 반복 과정을 통해 발전되었습니다. 이러한 특성으로 인해 C++는 다중 패러다임 프로그래밍 언어라고 합니다. C++에서는 기본 포인터, 배열, null 종료 문자열, 사용자 지정 데이터 구조 및 성능 향상에 큰 도움이 되지만 버그 및 복잡성 문제도 함께 발생할 수 있는 기타 기능들이 포함된 순수 절차적 C 스타일 프로그래밍을 수행할 수 있습니다.  C 스타일 프로그래밍은 이러한 위험이 크기 때문에 C++에 대한 한 가지 기본 목표는 형식이 안전하면서도 쉽게 쓰고, 확장하고, 유지 관리할 수 있는 프로그램을 만드는 것입니다. 초기에는 C++에서 개체 지행 프로그래밍과 같은 프로그래밍 패러다임을 채택하였습니다. 수년에 걸쳐 데이터 구조 및 알고리즘에 대한 고도의 테스트를 거친 표준 라이브러리와 함께 몇 가지 기능이 언어에 추가되었습니다. 이러한 추가 기능으로 최신 C++ 스타일이 구현되었습니다.

최신 C++는 다음을 강조합니다.

- 힙 또는 정적 전역 범위가 아닌 스택 기반 범위

- 명시적 형식 이름이 아닌 자동 형식 유추

- 원시 포인터가 아닌 스마트 포인터

- `std::string` 및 `std::wstring` 형식 (참조 [ \<문자열 >](../standard-library/string.md)) 대신 원시 `char[]` 배열입니다.

- [C + + 표준 라이브러리](../standard-library/cpp-standard-library-header-files.md) 컨테이너와 같은 `vector`하십시오 `list`, 및 `map` 원시 배열 또는 사용자 지정 컨테이너 대신 합니다. 참조 [ \<벡터 >](../standard-library/vector.md)합니다 [ \<목록 >](../standard-library/list.md), 및 [ \<지도 >](../standard-library/map.md)합니다.

- C + + 표준 라이브러리 [알고리즘](../standard-library/algorithm.md) 대신 수동으로 코딩 된 알고리즘이 있습니다.

- 보고서 및 핸들 오류 조건에 대한 예외

- 잠금 없음이라고 c + + 표준 라이브러리를 사용 하 여 스레드 간 통신 `std::atomic<>` (참조 [ \<원자성 >](../standard-library/atomic.md)) 다른 스레드 간 통신 메커니즘 대신 합니다.

- 인라인 [람다 함수](../cpp/lambda-expressions-in-cpp.md) 작은 함수를 개별적으로 구현 하는 대신 합니다.

- 범위 기반 for 루프를 사용 하는 배열, c + + 표준 라이브러리 컨테이너 및 Windows 런타임 형식의 컬렉션 보다 견고한 루프를 쓸 `for ( for-range-declaration : expression )`합니다. 핵심 언어 지원에 포함됩니다. 자세한 내용은 [범위에 대 한 문 (c + +)를 기준으로](../cpp/range-based-for-statement-cpp.md)입니다.

C++ 언어 자체도 발전하고 있습니다. 다음 코드 조각을 비교해 보십시오. 이 코드는 기존 C++의 방식을 보여 줍니다.

```cpp
#include <vector>

void f()
{
    // Assume circle and shape are user-defined types
    circle* p = new circle( 42 );
    vector<shape*> v = load_shapes();

    for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {
        if( *i && **i == *p )
            cout << **i << " is a match\n";
    }

    // CAUTION: If v's pointers own the objects, then you
    // must delete them all before v goes out of scope.
    // If v's pointers do not own the objects, and you delete
    // them here, any code that tries to dereference copies
    // of the pointers will cause null pointer exceptions.
    for( vector<circle*>::iterator i = v.begin();
            i != v.end(); ++i ) {
        delete *i; // not exception safe
    }

    // Don't forget to delete this, too.
    delete p;
} // end f()
```

다음은 최신 C++에서는 동일한 작업이 수행되는 방식입니다.

```cpp
#include <memory>
#include <vector>

void f()
{
    // ...
    auto p = make_shared<circle>( 42 );
    vector<shared_ptr<shape>> v = load_shapes();

    for( auto& s : v )
    {
        if( s && *s == *p )
        {
            cout << *s << " is a match\n";
        }
    }
}
```

최신 C++에서는 대신 스마트 포인터를 사용할 수 있으므로 new/delete 또는 명시적 예외 처리를 사용할 필요가 없습니다. 사용 하는 경우는 **자동** 형식 추론 하 고 [람다 함수](../cpp/lambda-expressions-in-cpp.md), 밀도 있게 코드를 더 빠르게 작성할 수 있습니다 및 더 잘 이해 합니다. 및 범위 기반 **에 대 한** 루프는 깔끔하고 사용 하기 쉬우며 C 스타일 보다 의도 하지 않은 오류 발생 우려가 적은 **에 대 한** 루프입니다. 상용구와 최소한의 코드 줄을 사용하여 응용 프로그램을 작성할 수 있습니다. 해당 코드를 예외와 메모리로부터 안전하게 유지할 수 있으며 할당/할당 해제 또는 오류 코드를 처리할 필요가 없습니다.

최신 C++는 두 가지 종류의 다형성, 즉, 템플릿을 통한 컴파일 타임과 상속 및 가상화를 통한 런타임을 통합합니다. 두 종류의 다형성을 혼합하여 더 뛰어난 효과를 제공할 수 있습니다. C + + 표준 라이브러리 템플릿 `shared_ptr` 해당 형식을 삭제를 달성 하기 위해 내부 가상 메서드를 사용 합니다. 템플릿이 더 나은 경우에는 다형성에 가상화를 과다 사용하지 마십시오. 템플릿은 매우 강력할 수 있습니다.

특히 대부분의 형식이 참조 형식이고 극히 일부만 값 형식인 관리되는 언어와 같은 다른 언어에서 C++로 전환한 경우, C++ 클래스는 기본적으로 값 형식이라는 것에 주의해야 합니다. 하지만 참조 형식으로 지정하여 개체 지향 프로그래밍을 지원하는 다형성 동작을 사용할 수 있습니다. 유용 정보: 값 형식은 메모리 및 레이아웃 컨트롤과 관련되어 있으며 참조 형식은 다형성을 지원하는 기본 클래스 및 가상 함수와 관련되어 있습니다. 기본적으로 값 형식을 복사할 수 있습니다. 각각은 복사 생성자와 복사 할당 연산자가 있습니다. 참조 형식을 지정할 때 클래스를 복사할 수 없도록 설정하고(복사 생성자와 복사 할당 연산자 사용 안 함) 다형성을 지원하는 가상 소멸자를 사용합니다. 값 형식은 또한 내용과 관련 있습니다. 즉 복사될 때 독립적인 값 두 개를 제공하여 따로 수정할 수 있습니다. 그러나 참조 형식은 개체의 종류를 나타내므로 다형 형식이라고도 합니다.

성능이 가장 중요해지면서 C++가 다시 부활하고 있습니다. 프로그래머의 생산성이 중요할 경우 Java와 C#과 같은 언어가 유용하지만 힘과 성능이 중요할 경우에는 한계성을 드러냅니다. 특히 하드웨어가 제한적인 장치에서는 C++가 가장 뛰어난 효율성과 성능을 제공합니다.

언어뿐만 아니라 개발 도구도 최신입니다. Visual Studio는 강력 하 고 효율적인 개발 주기의 모든 부분을 만듭니다. ALM(Application Lifecycle Management) 도구, IntelliSense와 같이 강화된 IDE 기능, XAML과 같이 도구 활용이 편한 메커니즘, 빌딩, 디버깅과 기타 도구가 포함됩니다.

이 설명서 부분에 포함된 문서에서는 현대적인 C++ 프로그램을 작성하는 데 가장 중요한 기능 및 기술에 대한 고급 지침 및 모범 사례를 제공합니다.

- [C + + 형식 시스템](../cpp/cpp-type-system-modern-cpp.md)

- [균일 초기화 및 생성자 위임](../cpp/uniform-initialization-and-delegating-constructors.md)

- [개체 수명 및 리소스 관리](../cpp/object-lifetime-and-resource-management-modern-cpp.md)

- [개체가 리소스 소유(RAII)](../cpp/objects-own-resources-raii.md)

- [스마트 포인터](../cpp/smart-pointers-modern-cpp.md)

- [컴파일 시간 캡슐화에 대 한 Pimpl](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)

- [컨테이너](../cpp/containers-modern-cpp.md)

- [알고리즘](../cpp/algorithms-modern-cpp.md)

- [문자열 및 I/O 서식 (최신 c + +)](../cpp/string-and-i-o-formatting-modern-cpp.md)

- [오류 및 예외 처리](../cpp/errors-and-exception-handling-modern-cpp.md)

- [ABI 경계의 이식성](../cpp/portability-at-abi-boundaries-modern-cpp.md)

자세한 내용은 StackOverflow 문서를 참조 하세요 [c + + 관용구는 C + + 11에서 사용 되지 않는](https://stackoverflow.com/questions/9299101/which-c-idioms-are-deprecated-in-c11)합니다.

## <a name="see-also"></a>참고자료

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[람다 식](../cpp/lambda-expressions-in-cpp.md)<br/>
[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)<br/>
[Visual C++ 언어 규칙](../visual-cpp-language-conformance.md)