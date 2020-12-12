---
description: '자세한 정보:/Zc: referenceBinding (참조 바인딩 규칙 적용)'
title: /Zc:referenceBinding(참조 바인딩 규칙 적용)
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: 7d094a2ec3ec680c463a7a756e70e02b9c40c07c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269161"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding(참조 바인딩 규칙 적용)

**/Zc: referenceBinding** 옵션이 지정 된 경우 컴파일러는 const가 아닌 lvalue 참조를 사용 하 여 임시에 바인딩할 수 없습니다.

## <a name="syntax"></a>Syntax

> **/Zc: referenceBinding**[ **-** ]

## <a name="remarks"></a>설명

**/Zc: referenceBinding** 이 지정 된 경우 컴파일러는 c + + 11 표준의 8.5.3 섹션을 따릅니다. 사용자 정의 형식 임시를 비 const lvalue 참조에 바인딩하는 식은 허용 되지 않습니다. 기본적으로 또는 **/zc: referenceBinding-** 이 지정 된 경우 컴파일러는 이러한 식을 Microsoft 확장으로 허용 하지만 수준 4 경고가 발생 합니다. 코드 보안, 이식성 및 규칙을 위해 **/zc: referenceBinding** 을 사용 하는 것이 좋습니다.

**/Zc: referenceBinding** 옵션은 기본적으로 해제 되어 있습니다. [/Permissive-](permissive-standards-conformance.md) 컴파일러 옵션은이 옵션을 암시적으로 설정 하지만 **/Zc: referencebinding-** 를 사용 하 여 재정의할 수 있습니다.

## <a name="example"></a>예제

이 샘플에서는 사용자 정의 형식의 임시를 비 const lvalue 참조에 바인딩할 수 있도록 하는 Microsoft 확장을 보여 줍니다.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

int main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Zc: referenceBinding** 을 포함 하도록 **추가 옵션** 속성을 수정한 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/Zc(규칙)](zc-conformance.md)<br/>
