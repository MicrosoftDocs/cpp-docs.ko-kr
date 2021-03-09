---
title: '오류: 새-삭제-형식 불일치'
description: 새 delete 유형 불일치 오류에 대 한 소스 예제 및 라이브 디버그 스크린샷.
ms.date: 03/02/2021
f1_keywords:
- new-delete-type-mismatch
helpviewer_keywords:
- new-delete-type-mismatch error
- AddressSanitizer error new-delete-type-mismatch
ms.openlocfilehash: 02ea69b16fbb18878fd46544488ac8f3e0d4e3b5
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471129"
---
# <a name="error-new-delete-type-mismatch"></a>오류: `new-delete-type-mismatch`

> 주소 Sanitizer 오류: 할당 취소 크기와 할당 크기가 다릅니다.

이 예제에서는만 `~Base` `~Derived` 호출 되 고는 호출 되지 않습니다. 소멸자가이 아니기 때문에 컴파일러는에 대 한 호출을 생성 합니다 `~Base()` `Base` **`virtual`** . 를 호출 하면 `delete b` 개체의 소멸자가 기본 정의에 바인딩됩니다. 이 코드는 빈 기본 클래스 (또는 Windows의 경우 1 바이트)를 삭제 합니다. 상속을 **`virtual`** 사용 하는 경우 소멸자 선언에 키워드가 없는 것은 일반적인 c + + 오류입니다.

## <a name="example---virtual-destructor"></a>예제-가상 소멸자

```cpp
// example1.cpp
// new-delete-type-mismatch error
#include <memory>
#include <vector>

struct T {
    T() : v(100) {}
    std::vector<int> v;
};

struct Base {};

struct Derived : public Base {
    T t;
};

int main() {
    Base *b = new Derived;

    delete b;  // Boom! 

    std::unique_ptr<Base> b1 = std::make_unique<Derived>();

    return 0;
}
```

다형성 기본 클래스는 소멸자를 선언 해야 합니다 **`virtual`** . 클래스에 가상 함수가 있는 경우 가상 소멸자가 있어야 합니다.

예제를 수정 하려면 다음을 추가 합니다.

```cpp
struct Base {
  virtual ~Base() = default;
}
```

이 예제를 빌드하고 테스트 하려면 Visual Studio 2019 버전 16.9 이상의 [개발자 명령 프롬프트](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)에서 다음 명령을 실행 합니다.

```cmd
cl example1.cpp /fsanitize=address /Zi
devenv /debugexe example1.exe
```

### <a name="resulting-error"></a>결과 오류

:::image type="content" source="media/new-delete-type-mismatch-example-1.png" alt-text="예 1에서 새-삭제-유형 불일치 오류를 표시 하는 디버거의 스크린샷":::

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
