---
description: '자세한 정보:/Zc: alignedNew (c + + 17 과도 맞춤 할당)'
title: /Zc:alignedNew(C++17 과다 정렬된 할당)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 149272e29a9b54f5b3ec7cddaaab8d3d969c0287
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114743"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew(C++17 과다 정렬된 할당)

**`new`** 최대 크기의 표준 맞춤 형식에 대 한 기본값 보다 큰 경계에 맞춘 c + + 17에 대 한 동적 메모리 할당을 지원 하도록 설정 합니다. 최대 **\_ 맞춤 \_ t**.

## <a name="syntax"></a>Syntax

> **/Zc: alignedNew** \[ -]

## <a name="remarks"></a>설명

MSVC 컴파일러 및 라이브러리는 C++ 17 표준 과다 정렬된 동적 메모리 할당을 지원합니다. **/Zc: alignedNew** 옵션을 지정 하면와 같은 동적 할당은 `new Example;`  `max_align_t` 모든 기본 형식에 필요한 가장 큰 맞춤 보다 큰 경우에도 예의 맞춤을 지정 합니다. **`new`** 미리 정의 된 매크로 **\_ \_ stdcpp \_ 기본 \_ 새 \_ 맞춤 \_ \_** 의 값으로 사용할 수 있는, 할당 된 형식의 맞춤이 원래 연산자에 의해 보장 되는 맞춤 보다 많을 경우 문은 `new Example;` `::operator new(size_t)` c + + 14 에서처럼를 호출 합니다. 맞춤이 **\_ \_ stdcpp \_ 기본 \_ 새 \_ \_ 맞춤 \_** 보다 큰 경우 구현은 대신를 사용 하 여 메모리를 가져옵니다 `::operator new(size_t, align_val_t)` . 마찬가지로, 과다 정렬된 형식을 삭제하면 `::operator delete(void*, align_val_t)` 또는 크기가 지정된 삭제 서명 `::operator delete(void*, size_t, align_val_t)`가 호출됩니다.

**/Zc:alignedNew** 옵션은 [/std:c++17](std-specify-language-standard-version.md) 또는 [/std:c++latest](std-specify-language-standard-version.md)가 활성화된 경우에만 사용할 수 있습니다. **/std:c++17** 또는 **/std:c++latest** 에서 **/Zc:alignedNew** 는 기본적으로 ISO C++17 표준을 준수하도록 활성화되어 있습니다. 연산자를 구현 하 **`new`** 고 **`delete`** 과도 하 게 정렬 된 할당을 지 원하는 경우에는 c + + 17 모드에서이 코드가 더 이상 필요 하지 않을 수 있습니다. 이 옵션을 해제 하 고의 c + + 14 동작으로 **`new`** 되돌리고 **`delete`** **/std:: c + + 17** 또는 **/std: c + + 최신** 를 사용 하는 경우 **/zc: alignedNew-** 를 지정 합니다. 연산자 **`new`** 를 구현 **`delete`** 하지만 매개 변수가 있는 오버 로드 된 연산자 및 오버 로드를 구현할 준비가 되지 않은 경우 **`new`** **`delete`** `align_val_t` **/zc: alignedNew-** 옵션을 사용 하 여 컴파일러 및 표준 라이브러리에서 오버 로드 된 오버 로드에 대 한 호출을 생성 하지 않도록 합니다. [/permissive-](permissive-standards-conformance.md) 옵션은 **/Zc:alignedNew** 의 기본 설정을 변경하지 않습니다.

**/Zc:alignedNew** 에 대한 지원은 Visual Studio 2017 버전 15.5부터 제공됩니다.

## <a name="example"></a>예제

이 샘플은 **`new`** **`delete`** **/zc: alignedNew** 옵션이 설정 된 경우 연산자 및 연산자가 동작 하는 방법을 보여 줍니다.

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

이 출력은 32비트 빌드에서 일반적입니다. 포인터 값은 애플리케이션이 메모리에서 실행되는 위치에 따라 다릅니다.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Visual C++의 규칙과 관련된 문제에 대한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)를 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Zc:alignedNew** 또는 **/Zc:alignedNew-** 를 포함하도록 **추가 옵션** 속성을 수정한 다음, **확인** 을 선택합니다.

## <a name="see-also"></a>참고 항목

[/Zc(규칙)](zc-conformance.md)
