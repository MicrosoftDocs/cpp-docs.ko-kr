---
title: /D(전처리기 정의)
ms.date: 09/18/2019
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: 7c8a500820c8cc4655c409f4628d72a69acafa5a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040940"
---
# <a name="d-preprocessor-definitions"></a>/D(전처리기 정의)

소스 파일에 대한 전처리 기호를 정의합니다.

## <a name="syntax"></a>구문

> **/D** \[ ]_name_ \[ `=` \| `#` \[ { *string* \| *number* }]] \
> **/D** \[ ] `"` _name_ \[ `=` \| `#` \[ { *string* \| *number* }]]`"`

## <a name="remarks"></a>설명

이 기호를 `#if` 또는 `#ifdef`와 함께 사용하여 조건에 따라 소스 코드를 컴파일할 수 있습니다. 기호 정의는 코드에서 다시 정의 되거나 지시문에 의해 코드에서 정의 되지 않을 때까지 계속 적용 됩니다 `#undef` .

**/D** 는 `#define` 소스 코드 파일의 시작 부분에 있는 지시문과 동일한 효과를 가집니다. 차이점은 **/d** 는 명령줄에서 따옴표를 제거 하 고 지시문은 해당 따옴표를 유지 한다는 것입니다 `#define` . **/D** 와 기호 사이에 공백이 있을 수 있습니다. 기호와 등호 사이에 공백이 나 등호와 할당 된 값 사이에는 공백이 있을 수 없습니다.

기호와 관련된 값은 기본적으로 1입니다. 예를 들어 `/D name`는 `/D name=1`와 같습니다. 이 문서의 끝에 있는 예제에서는의 정의가 `TEST` 인쇄로 표시 됩니다 `1` .

를 사용 하 여 컴파일하면 `/D name=` 기호 *이름* 에 연결 된 값이 포함 되지 않습니다. 기호를 사용해 조건에 따라 코드를 컴파일할 수 있지만 그렇지 않은 경우 기호가 어떤 값으로도 계산되지 않습니다. 예제에서를 사용 하 여 컴파일하면 `/DTEST=` 오류가 발생 합니다. 이 동작은 값을 사용하거나 사용하지 않을 때에도 `#define`을 사용할 때의 동작과 비슷합니다.

**/D** 옵션은 함수 형식 매크로 정의를 지원 하지 않습니다. 명령줄에서 정의할 수 없는 정의를 삽입 하려면 [/fi (강제 포함 파일 이름 지정)](fi-name-forced-include-file.md) 컴파일러 옵션을 고려 합니다.

명령줄에서 **/d** 를 여러 번 사용 하 여 추가 기호를 정의할 수 있습니다. 동일한 기호가 두 번 이상 정의 된 경우 마지막 정의가 사용 됩니다.

이 명령은 TEST.c에서 DEBUG 기호를 정의합니다.

```cmd
CL /DDEBUG TEST.C
```

이 명령은 TEST.c에 있는 모든 `__far` 키워드를 제거합니다.

```cmd
CL /D __far= TEST.C
```

**CL** 환경 변수는 등호를 포함 하는 문자열로 설정할 수 없습니다. **/D** 를 **CL** 환경 변수와 함께 사용 하려면 등호 대신 숫자 기호 ()를 지정 해야 합니다 `#` .

```cmd
SET CL=/DTEST#0
```

명령 프롬프트에서 전처리 기호를 정의하면 컴파일러 구문 분석 규칙과 셸 구문 분석 규칙을 모두 수행하는 것이 좋습니다. 예를 들어 프로그램에서 백분율 기호 전처리 기호 ()를 정의 하려면 `%` 명령 프롬프트에서 두 개의 백분율 기호 문자 ()를 지정 `%%` 합니다. 하나만 지정 하는 경우 구문 분석 오류가 내보내집니다.

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. 왼쪽 창에서 **구성 속성**, **C/c + +**, **전처리기**를 선택 합니다.

1. 오른쪽 창에서 **전처리기 정의** 속성의 오른쪽 열에 있는 드롭다운 메뉴를 열고 **편집**을 선택 합니다.

1. **전처리기 정의** 대화 상자에서 하나 이상의 정의를 한 줄에 하나씩 추가 하거나, 수정 하거나, 삭제 합니다. **확인**을 선택하여 변경 내용을 저장합니다.

   여기에서 지정 하는 정의에 '/D ' 옵션 접두사를 포함할 필요가 없습니다. 속성 페이지에서 정의는 세미콜론 ()으로 구분 됩니다 `;` .

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>을 참조하세요.

## <a name="example"></a>예제

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
#include <stdio.h>

int main( )
{
#ifdef TEST
    printf_s("TEST defined %d\n", TEST);
#else
    printf_s("TEST not defined\n");
#endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)\
[/FI (강제 포함 파일 이름)](fi-name-forced-include-file.md)\
[/U,/u (기호 정의 해제)](u-u-undefine-symbols.md)\
[#undef 지시문 (C/c + +)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[#define 지시문 (C/c + +)](../../preprocessor/hash-define-directive-c-cpp.md)
