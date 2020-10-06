---
title: /RTC(런타임 오류 검사)
description: 런타임 오류 검사에 대 한 Microsoft C/c + + 컴파일러/RTC 옵션입니다.
ms.date: 07/31/2020
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
ms.openlocfilehash: 888a81d0d5c21b0b85420a43d534c5b2742aa082
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765239"
---
# <a name="rtc-run-time-error-checks"></a>`/RTC` (런타임 오류 검사)

[Runtime_checks](../../preprocessor/runtime-checks.md) pragma와 함께 런타임 오류 검사 기능을 사용 하거나 사용 하지 않도록 설정 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

> **`/RTC1`**\
> **`/RTCc`**\
> **`/RTCs`**\
> **`/RTCu`**

## <a name="arguments"></a>인수

**`/RTC1`**<br/>
와 동일 **`/RTCsu`** 합니다.

**`/RTCc`**<br/>
더 작은 데이터 형식에 값을 할당 하 고 데이터 손실을 발생 시킬 때 보고 합니다. 예를 들어 **`short`** 의 형식 값 `0x0101` 이 형식의 변수에 할당 되었는지 여부를 보고 **`char`** 합니다.

이 옵션은 잘라내야 하는 상황을 보고할 수 있습니다. 예를 들어의 처음 8 비트를로 반환 하려고 합니다 **`int`** **`char`** . **`/RTCc`** 는 할당으로 인해 정보 손실이 발생 하는 경우 런타임 오류가 발생 하므로 런타임 오류를 방지 하는 데 필요한 정보를 먼저 마스크 합니다. 예를 들면 다음과 같습니다.

```C
#include <crtdbg.h>

char get8bits(unsigned value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

는 **`/RTCc`** 표준을 준수 하는 코드를 거부 하므로 c + + 표준 라이브러리에서 지원 되지 않습니다. **`/RTCc`** 및 c + + 표준 라이브러리를 사용 하는 코드에서 컴파일러 오류 [C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md)발생할 수 있습니다. 경고를 표시 `_ALLOW_RTCc_IN_STL` 하도록 정의 하 고 옵션을 사용할 수 있습니다 **`/RTCc`** .

**`/RTCs`**<br/>
다음과 같이 스택 프레임 런타임 오류 검사를 사용 하도록 설정 합니다.

- 지역 변수를 0이 아닌 값으로 초기화 합니다. 이 옵션은 디버그 모드에서 실행할 때 표시 되지 않는 버그를 식별 하는 데 도움이 됩니다. 릴리스 빌드와 비교할 때 스택 변수에 여전히 디버그 빌드에서 0 값이 있을 가능성이 높습니다. 릴리스 빌드에서 스택 변수의 컴파일러 최적화 때문입니다. 프로그램에서 스택의 영역을 사용한 후에는 컴파일러에서 0으로 다시 설정 되지 않습니다. 즉, 나중에 동일한 스택 영역을 사용 하기 위해 발생 하는 초기화 되지 않은 스택 변수는이 스택 메모리의 이전 사용에서 남은 값을 반환할 수 있습니다.

- 배열과 같은 지역 변수의 오버런 및 언더런를 검색 합니다. **`/RTCs`** 는 구조체 내의 컴파일러 패딩에서 발생 하는 메모리에 액세스할 때의 오버런을 검색 하지 않습니다. 안쪽 여백은 [`align`](../../cpp/align-cpp.md) , [ `/Zp` (구조체 멤버 맞춤)](zp-struct-member-alignment.md)또는을 사용 하 여 발생 [`pack`](../../preprocessor/pack.md) 하거나, 컴파일러가 안쪽 여백을 추가 해야 하는 것과 같은 방식으로 구조체 요소를 정렬 하는 경우에 발생할 수 있습니다.

- 스택 포인터를 확인 하 여 스택 포인터 손상을 감지 합니다. 호출 규칙 불일치로 인해 스택 포인터가 손상 될 수 있습니다. 예를 들어 함수 포인터를 사용 하는 경우로 내보내지는 DLL에서 함수를 호출 하지만, [`__stdcall`](../../cpp/stdcall.md) 함수에 대 한 포인터를로 선언 합니다 [`__cdecl`](../../cpp/cdecl.md) .

**`/RTCu`**<br/>
초기화 되지 않은 변수를 사용 하는 경우를 보고 합니다. 예를 들어 경고 C4701를 생성 하는 명령은에서 런타임 오류를 생성할 수도 있습니다 **`/RTCu`** . [컴파일러 경고 (수준 1 및 수준 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) 를 생성 하는 명령은에서 런타임 오류를 생성 **`/RTCu`** 합니다.

그러나 다음 코드 조각을 고려 하십시오.

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

변수가 초기화 될 수 있는 경우 런타임에에 의해 보고 되지 않습니다 **`/RTCu`** . 예를 들어 변수가 포인터를 통해 별칭이 지정 된 후 컴파일러는 변수를 추적 하지 않으며 초기화 되지 않은 사용을 보고 합니다. 실제로 해당 주소를 가져와 변수를 초기화할 수 있습니다. **`&`** 이 경우 연산자는 대입 연산자 처럼 작동 합니다.

## <a name="remarks"></a>설명

런타임 오류 검사를 통해 실행 중인 코드에서 문제를 찾을 수 있습니다. 자세한 내용은 [방법: 네이티브 런타임 검사 사용](/visualstudio/debugger/how-to-use-native-run-time-checks)을 참조 하세요.

명령줄에서 둘 이상의 옵션을 지정할 수 있습니다 **`/RTC`** . 옵션 인수를 결합할 수 있습니다. 예를 들어, **`/RTCcu`** 는와 같습니다 **`/RTCc /RTCu`** .

컴파일러 옵션 중 하나를 사용 하 여 명령줄에서 프로그램을 컴파일하는 경우 **`/RTC`** [`optimize`](../../preprocessor/optimize.md) 코드의 모든 pragma 명령은 자동으로 실패 합니다. 런타임 오류 검사가 릴리스 (최적화 됨) 빌드에서 유효 하지 않기 때문입니다.

**`/RTC`** 개발 빌드에 사용 **`/RTC`** 릴리스 빌드에는를 사용 하지 마세요. **`/RTC`** 는 컴파일러 최적화 ([ `/O` 옵션 (코드 최적화)](o-options-optimize-code.md))와 함께 사용할 수 없습니다. 로 빌드된 프로그램 이미지는 **`/RTC`** 를 사용 하 여 빌드된 이미지 **`/Od`** (빌드 보다 최대 5% 느림) 보다 약간 더 크고 약간 느립니다 **`/Od`** .

`__MSVC_RUNTIME_CHECKS`전처리기 지시문은 또는 옵션을 사용할 때 정의 됩니다 **`/RTC`** [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **코드 생성** 속성 페이지를 선택 합니다.

1. **기본 런타임 검사** 또는 **더 작은 형식 검사**속성 중 하나 또는 둘 다를 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 속성을 참조하십시오.

## <a name="see-also"></a>참조

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)<br/>
[방법: 네이티브 런타임 검사 사용](/visualstudio/debugger/how-to-use-native-run-time-checks)
