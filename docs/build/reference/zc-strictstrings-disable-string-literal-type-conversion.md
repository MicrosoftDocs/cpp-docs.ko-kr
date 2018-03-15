---
title: "/Zc: strictstrings (문자열 리터럴 형식 변환 사용 안 함) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs:
- C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61ae45d6a067b45d625055d92900b17e69a366e7
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2018
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings(문자열 리터럴 형식 변환 사용 안 함)

지정한 경우 컴파일러에는 문자열 리터럴을 사용하여 초기화한 포인터에 대한 엄격한 `const` 한정 규칙이 필요합니다.

## <a name="syntax"></a>구문

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>설명

경우 **/zc: strictstrings** 를 지정한 경우 컴파일러는 표준 c + + `const` 문자열 리터럴 형식에 대 한 자격 ' 배열을 `const char`' 또는 ' 배열을 `const wchar_t`' 선언에 따라, 합니다. 문자열 리터럴은 변경 불가능하고 문자열 리터럴 중 하나의 내용을 수정하려고 하면 런타임에 액세스 위반 오류가 발생합니다. 문자열 포인터를 `const`로 선언하여 문자열 리터럴을 사용하여 초기화하거나 명시적 `const_cast`를 사용하여 비`const` 포인터를 초기화해야 합니다. 기본적으로 또는 **/Zc:strictStrings-** 컴파일러는 표준 c + +를 적용 하지 않는 지정 된 `const` 문자열 리터럴을 사용 하 여 초기화 된 문자열 포인터에 대 한 자격입니다.

**/zc: strictstrings** 옵션은 기본적으로 해제 되어 있습니다. [관대 한 /-](permissive-standards-conformance.md) 컴파일러 옵션에는 암시적으로이 옵션을 설정 하지만 사용 하 여 재정의할 수 있습니다 **/Zc:strictStrings-**합니다.

사용 하 여 **/zc: strictstrings** 잘못 된 코드의 컴파일을 방지 하려면 옵션입니다. 다음 예제에서는 간단한 선언 오류가 런타임에 충돌을 어떻게 발생시키는지 보여줍니다. 

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

때 **/zc: strictstrings** 는 동일한 코드의 선언에는 오류를 보고 사용 하도록 설정 `str`합니다.

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

`auto`를 사용하여 문자열 포인터를 선언하면 컴파일러에서는 올바른 `const` 포인터 형식 선언을 만듭니다. `const` 포인터의 내용을 수정하려는 시도는 컴파일러에서 오류로 보고합니다.

> [!NOTE]
> c + + 표준 라이브러리 [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] 지원 하지 않습니다는 **/zc: strictstrings** 디버그에서 컴파일러 옵션을 빌드합니다. 여러 [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) 빌드에 대 한 오류 출력을이 원인일 수 있습니다.

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)합니다.

1. 선택 된 **구성 속성** > **C/c + +** > **명령줄** 속성 페이지.

1. 수정 된 **추가 옵션** 포함할 속성을 **/zc: strictstrings** 선택한 후 **확인**합니다.

## <a name="see-also"></a>참고 항목

[/Zc(규칙)](../../build/reference/zc-conformance.md)<br/>
