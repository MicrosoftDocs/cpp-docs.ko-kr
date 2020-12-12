---
description: 자세히 알아보기:/clr 제한
title: /clr 제한
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: eb74aea8f1d6fcae4738f17f5fae2a4761350341
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193008"
---
# <a name="clr-restrictions"></a>/clr 제한

**/clr** 사용 시 다음과 같은 제한 사항이 적용됩니다.

- 정형 예외 처리기는 **/clr** 을 사용하여 컴파일할 때 `_alloca` 사용에 대한 제한이 있습니다. 자세한 내용은 [_alloca](../../c-runtime-library/reference/alloca.md)를 참조하세요.

- **/clr** 을 사용한 런타임 오류 확인은 유효하지 않습니다. 자세한 내용은 [방법: 네이티브 런타임 검사 기능 사용](/visualstudio/debugger/how-to-use-native-run-time-checks)을 참조하세요.

- 표준 C++ 구문만 사용하는 프로그램을 컴파일하기 위해 **/clr** 을 사용하는 경우 인라인 어셈블리 사용 시 다음 지침이 적용됩니다.

  - 기본 스택 레이아웃에 대한 지식을 전제로 하며 현재 함수의 범위를 벗어난 규칙 또는 컴퓨터에 대한 기타 하위 수준 정보를 호출하는 인라인 어셈블리 코드는 해당 지식이 관리형 함수의 스택 프레임에 적용되면 실패할 수 있습니다. 인라인 어셈블리 코드를 포함하는 함수는 마치 **/clr** 없이 컴파일된 별도의 모듈에 배치된 것처럼 비관리형 함수로 생성됩니다.

  - copy-constructed 함수 매개 변수를 전달하는 인라인 어셈블리 코드는 지원되지 않습니다.

- [vprintf 함수](../../c-runtime-library/vprintf-functions.md)는 **/clr** 로 컴파일된 프로그램에서 호출할 수 없습니다.

- [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) 한정자는 /clr 아래에서 무시됩니다.

- [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)로 설정된 변환기 함수는 비관리 코드의 catch에만 적용됩니다. 자세한 내용은 [예외 처리](../../extensions/exception-handling-cpp-component-extensions.md)를 참조하세요.

- **/clr** 아래에서 함수 포인터를 비교할 수 없습니다.

- 완전히 프로토타입화되지 않은 함수는 **/clr** 아래에서 사용할 수 없습니다.

- 다음 컴파일러 옵션은 **/clr** 을 지원하지 않습니다.

  - **/EHsc** 및 **/EHs**(**/clr** 은 **/EHa** 를 의미([/EH(예외 처리 모델)](eh-exception-handling-model.md) 참조)

  - **/fp:strict** 및 **/fp:except**([/fp(부동 소수점 동작 지정)](fp-specify-floating-point-behavior.md) 참조)

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [Zi](z7-zi-zi-debug-information-format.md)

- `_STATIC_CPPLIB` 전처리기 정의(`/D_STATIC_CPPLIB`)와 **/clr** 컴파일러 옵션의 조합은 지원되지 않습니다. 이 정의는 애플리케이션이 정적 다중 스레드 C++ 표준 라이브러리에 연결하게 만드는데, 이는 지원되지 않습니다. 자세한 내용은 [/MD, /MT, /LD(런타임 라이브러리 사용)](md-mt-ld-use-run-time-library.md) 토픽을 참조하세요.

- **/Zi** 를 **/clr** 에 사용하면 성능에 영향이 있습니다. 자세한 내용은 [/Zi](z7-zi-zi-debug-information-format.md)를 참조하세요.

- [/Zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md) 를 지정 하지 않고 .NET Framework 출력 루틴에 와이드 문자를 전달 하는 경우 (으)로 문자를 캐스팅 하지 않고 **`__wchar_t`** 출력이로 표시 되도록 `unsigned short int` 합니다. 예를 들어:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- 함수가 `#pragma` [unmanaged](../../preprocessor/managed-unmanaged.md) 아래에 있거나 네이티브로 컴파일되지 않는 한, **/clr** 로 컴파일할 때 [/GS](gs-buffer-security-check.md)가 무시되며, 이 경우 컴파일러가 기본적으로 해제되는 C4793 경고를 생성합니다.

- 관리형 애플리케이션의 함수 시그니처 요구 사항에 대한 [/ENTRY](entry-entry-point-symbol.md)를 참조하세요.

- **/openmp** 및 **/clr** 로 컴파일된 애플리케이션은 단일 appdomain 프로세스에서만 실행할 수 있습니다.  자세한 내용은 [/openmp(OpenMP 2.0 지원 활성화)](openmp-enable-openmp-2-0-support.md)를 참조하세요.

- 가변 인수 번호(varargs)를 사용하는 함수는 네이티브 함수로 생성됩니다. 가변 인수 위치의 관리되는 데이터 형식은 네이티브 형식으로 마샬링됩니다. <xref:System.String?displayProperty=fullName> 형식은 실제로 와이드 문자 문자열이긴 하지만, 단일 바이트 문자열로 마샬링됩니다. 따라서 printf 지정자가 %S(wchar_t*)인 경우 %s 문자열으로 마샬링합니다.

- va_arg 매크로를 사용하는 경우 **/clr:pure** 로 컴파일할 때 예기치 않은 결과가 발생할 수 있습니다. 자세한 내용은 [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)를 참조하세요. **/clr:pure** 및 **/clr:safe** 컴파일러 옵션은 Visual Studio 2015에서는 더 이상 사용되지 않으며 Visual Studio 2017 이상에서는 지원되지 않습니다. “순수” 또는 “안전”해야 하는 코드는 C#으로 포팅해야 합니다.

- 관리 코드에서는 스택을 탐색하여 매개 변수 정보(함수 인수)를 얻는 함수를 호출하면 안 됩니다. P/Invoke 레이어는 이 정보를 스택의 더 아래쪽에 배치합니다.  예를 들어 프록시/스텁을 **/clr** 로 컴파일하지 마세요.

- 가능한 경우에는 함수가 관리 코드로 컴파일되지만, 모든 C++ 구문을 관리 코드로 변환할 수 있는 것은 아닙니다.  이는 함수별로 결정됩니다. 함수의 특정 부분을 관리 코드로 변환할 수 없는 경우 함수 전체가 네이티브 코드로 변환됩니다. 다음은 컴파일러가 관리 코드를 생성하지 못하게 차단하는 사례입니다.

  - 컴파일러에서 생성한 썽크 또는 도우미 함수. 네이티브 썽크는 가상 함수 호출을 포함하여 함수 포인터를 통해 모든 함수 호출에 대해 생성됩니다.

  - `setjmp` 또는 `longjmp`를 호출하는 함수

  - 특정 내장 루틴을 사용하여 머신 리소스를 직접 조작하는 함수. 예를 들어 `__enable` 및 `__disable`, `_ReturnAddress` 및 `_AddressOfReturnAddress` 또는 멀티미디어 내장 함수를 사용하면 모두 네이티브 코드가 됩니다.

  - `#pragma unmanaged` 지시문을 따르는 함수. (반대로 `#pragma managed`도 지원됩니다.)

  - 정렬된 형식, `__declspec(align(...))`을 사용하여 선언된 형식을 포함하는 함수

## <a name="see-also"></a>참고 항목

- [/clr(공용 언어 런타임 컴파일)](clr-common-language-runtime-compilation.md)
