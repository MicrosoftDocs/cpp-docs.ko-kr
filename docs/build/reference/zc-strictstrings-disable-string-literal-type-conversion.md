---
description: '자세히 알아보기: `/Zc:strictStrings` (문자열 리터럴 형식 변환 사용 안 함)'
title: /Zc:strictStrings(문자열 리터럴 형식 변환 사용 안 함)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: 38c0ac2fe69acd81762fbf26797eece659ee63a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269057"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>`/Zc:strictStrings` (문자열 리터럴 형식 변환 사용 안 함)

지정 된 경우 컴파일러는 **`const`** 문자열 리터럴을 사용 하 여 초기화 된 포인터에 대해 엄격한 정규화 규칙을 요구 합니다.

## <a name="syntax"></a>Syntax

> **`/Zc:strictStrings`**[**`-`**]

## <a name="remarks"></a>설명

**`/Zc:strictStrings`** 이 지정 된 경우 컴파일러는 **`const`** 선언에 따라 문자열 리터럴에 대 한 표준 c + + 한정자를 ' 배열 `const char` ' 또는 ' 배열 ' 형식의 형식으로 적용 `const wchar_t` 합니다. 문자열 리터럴은 변경 불가능하고 문자열 리터럴 중 하나의 내용을 수정하려고 하면 런타임에 액세스 위반 오류가 발생합니다. 문자열 포인터를로 선언 하 여 **`const`** 문자열 리터럴을 사용 하 여 초기화 하거나 명시적를 사용 **`const_cast`** 하 여 비 포인터를 초기화 해야 합니다 **`const`** . 기본적으로 또는 **`/Zc:strictStrings-`** 이 지정 된 경우 컴파일러는 **`const`** 문자열 리터럴을 사용 하 여 초기화 된 문자열 포인터에 대해 표준 c + + 한정자를 적용 하지 않습니다.

**`/Zc:strictStrings`** 옵션은 기본적으로 해제 되어 있습니다. [`/permissive-`](permissive-standards-conformance.md)컴파일러 옵션은이 옵션을 암시적으로 설정 하지만을 사용 하 여 재정의할 수 있습니다 **`/Zc:strictStrings-`** .

잘못 된 **`/Zc:strictStrings`** 코드의 컴파일을 방지 하려면 옵션을 사용 합니다. 다음 예제에서는 간단한 선언 오류가 런타임에 충돌을 어떻게 발생시키는지 보여줍니다.

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

**`/Zc:strictStrings`** 을 사용 하는 경우 동일한 코드가의 선언에서 오류를 보고 합니다 `str` .

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

를 사용 하 여 문자열 포인터를 선언 하는 경우 **`auto`** 컴파일러는 올바른 **`const`** 포인터 형식 선언을 만듭니다. 포인터의 내용을 수정 하려는 시도는 **`const`** 컴파일러에서 오류로 보고 됩니다.

> [!NOTE]
> Visual Studio 2013의 c + + 표준 라이브러리는 **`/Zc:strictStrings`** 디버그 빌드에서 컴파일러 옵션을 지원 하지 않습니다. 빌드 출력에 여러 [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) 오류가 표시 되는 경우이 문제가 발생할 수 있습니다.

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 포함 하도록 **추가 옵션** 속성을 수정한 **`/Zc:strictStrings`** 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[`/Zc` 규칙](zc-conformance.md)<br/>
