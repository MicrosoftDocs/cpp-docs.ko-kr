---
description: 다음에 대 한 자세한 정보:/H (외부 이름 길이 제한)
title: /H(외부 이름 길이 제한)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: 5df4c4765cc4917e6914eab0b4818c34fceea853
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200080"
---
# <a name="h-restrict-length-of-external-names"></a>/H(외부 이름 길이 제한)

더 이상 사용되지 않습니다. 외부 이름의 길이를 제한 합니다.

## <a name="syntax"></a>Syntax

> **/H**<em>번호</em>

## <a name="arguments"></a>인수

*number*<br/>
프로그램에서 허용 되는 외부 이름의 최대 길이를 지정 합니다.

## <a name="remarks"></a>설명

기본적으로 외부 (공용) 이름의 길이는 2047 자입니다. 이는 C 및 c + + 프로그램에 적용 됩니다. **/H** 를 사용 하면 식별자의 허용 되는 최대 길이만 줄일 수 있고 증가 하지는 않습니다. **/H** 와 *number* 사이의 공백은 선택 사항입니다.

프로그램에 *number* 보다 긴 외부 이름이 포함 된 경우 추가 문자는 무시 됩니다. **/H** 를 사용 하지 않고 프로그램을 컴파일하는 경우 및 식별자에 2047 자 이상이 포함 되어 있으면 컴파일러는 [심각한 오류 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)를 생성 합니다.

길이 제한에는 컴파일러에서 생성 된 선행 밑줄 ( **\_** ) 또는 기호 ()가 포함 됩니다 **\@** . 이러한 문자는 식별자의 일부 이며 중요 한 위치를 사용 합니다.

- 컴파일러는 **\_** (기본값) 및 호출 규칙에 의해 수정 된 이름에 선행 밑줄 ()을 추가 하 **`__cdecl`** **`__stdcall`** 고 **\@** 호출 규칙에 의해 수정 된 이름에 선행 기호 ()를 추가 합니다 **`__fastcall`** .

- 컴파일러는 및 호출 규칙에 의해 수정 된 이름에 인수 크기 정보를 추가 **`__fastcall`** **`__stdcall`** 하 고 c + + 이름에 형식 정보를 추가 합니다.

**/H** 는 다음과 같이 유용 합니다.

- 혼합 언어 또는 이식 가능한 프로그램을 만드는 경우

- 외부 식별자의 길이에 제한을 적용 하는 도구를 사용 하는 경우

- 기호가 디버그 빌드에서 사용 하는 공간 크기를 제한 하려는 경우

다음 예에서는 식별자 길이가 너무 많이 제한 되는 경우 **/h** 를 사용 하 여 실제로 오류를 발생 시킬 수 있는 방법을 보여 줍니다.

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

또한 미리 정의 된 컴파일러 식별자로 인해 **/h** 옵션을 사용할 때 주의 해야 합니다. 최대 식별자 길이가 너무 작은 경우 미리 정의 된 특정 식별자는 물론 특정 라이브러리 함수 호출을 확인할 수 없습니다. 예를 들어 함수를 `printf` 사용 하 고 $ **5** 옵션을 컴파일 시간에 지정 하면 기호 **_prin** 을 참조 하기 위해 생성 되 `printf` 고이는 라이브러리에서 찾을 수 없습니다.

**/H** 를 사용 하는 것은 [/Gl (전체 프로그램 최적화)](gl-whole-program-optimization.md)과 호환 되지 않습니다.

**/H** 옵션은 Visual Studio 2005 이후부터 사용 되지 않습니다. 최대 길이 제한이 증가 하 고 **/h** 가 더 이상 필요 하지 않습니다. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별](compiler-options-listed-by-category.md)목록에서 **사용 되지 않는 컴파일러 옵션** 을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
