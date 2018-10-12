---
title: CRT 라이브러리 기능 | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0864c87b33937fe18c3e4c3083e63bde23ac06
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092247"
---
# <a name="crt-library-features"></a>CRT 라이브러리 기능

이 항목에서는 C 런타임 라이브러리 및 관련 컴파일러 옵션과 전처리기 지시문을 구성하는 다양한 .lib 파일에 대해 설명합니다.

## <a name="c-run-time-libraries-crt"></a>C 런타임 라이브러리(CRT)

CRT(C 런타임) 라이브러리는 ISO C99 표준 라이브러리를 통합하는 C++ 표준 라이브러리의 일부입니다. CRT를 구현하는 Visual C++ 라이브러리는 네이티브 코드 개발 및 혼합된 네이티브와 관리 코드를 모두 지원합니다. 모든 버전의 CRT는 다중스레드 개발을 지원합니다. 대부분의 라이브러리는 라이브러리를 코드에 직접 연결하는 정적 연결이나 코드에서 공용 DLL 파일을 사용할 수 있도록 하는 동적 연결을 모두 지원합니다.

Visual Studio 2015부터 CRT는 새로운 이진 파일로 리팩터링되었습니다. UCRT(유니버설 CRT)에는 표준 C99 CRT 라이브러리에서 내보낸 전역 변수 및 함수가 포함됩니다. UCRT는 이제 Windows 구성 요소이며 Windows 10의 일부로 제공됩니다. 이제 정적 라이브러리, DLL 가져오기 라이브러리 및 UCRT에 대한 헤더 파일이 Windows 10 SDK에 있습니다. Visual C++를 설치하면 Visual Studio 설치에서 UCRT를 사용하는 데 필요한 Windows 10 SDK의 하위 집합을 설치합니다. Visual Studio 2015 이상 버전에서 지원하는 모든 Windows 버전에서 UCRT를 사용할 수 있습니다. Windows 10이 아닌 지원되는 다른 버전의 Windows에 대해 vcredist를 사용하여 재배포할 수 있습니다. 자세한 내용은 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)을 참조하세요.

다음 표에는 UCRT를 구현하는 라이브러리가 나열되어 있습니다.

|라이브러리|관련 DLL|특성|옵션|전처리기 지시문|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt.lib|없음|코드에 UCRT를 정적으로 연결합니다.|**/MT**|_MT|
|libucrtd.lib|없음|정적 연결을 위한 UCRT의 디버그 버전입니다. 재배포할 수 없습니다.|**/MTd**|_DEBUG, _MT|
|ucrt.lib|ucrtbase.dll|UCRT에 대한 DLL 가져오기 라이브러리입니다.|**/MD**|_MT, _DLL|
|ucrtd.lib|ucrtbased.dll|UCRT의 디버그 버전에 대한 DLL 가져오기 라이브러리입니다. 재배포할 수 없습니다.|**/MDd**|_DEBUG, _MT, _DLL|

vcruntime 라이브러리에는 예외 처리 및 디버깅 지원, 런타임 검사 및 형식 정보, 구현 세부 정보 및 특정 확장된 라이브러리 기능 등 Visual C++ CRT 구현 관련 코드가 포함됩니다. 이 라이브러리는 사용된 컴파일러 버전에 따라 다릅니다.

다음 표에는 vcruntime 라이브러리를 구현하는 라이브러리가 나열되어 있습니다.

|라이브러리|관련 DLL|특성|옵션|전처리기 지시문|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime.lib|없음|코드에 정적으로 연결합니다.|**/MT**|_MT|
|libvcruntimed.lib|없음|정적 연결에 대한 디버그 버전입니다. 재배포할 수 없습니다.|**/MTd**|_MT, _DEBUG|
|vcruntime.lib|vcruntime\<version>.dll|vcruntime에 대한 DLL 가져오기 라이브러리입니다.|**/MD**|_MT, _DLL|
|vcruntimed.lib|vcruntime\<version>d.dll|디버그 vcruntime에 대한 DLL 가져오기 라이브러리입니다. 재배포할 수 없습니다.|**/MDd**|_DEBUG, _MT, _DLL|

> [!NOTE]
> UCRT 리팩터링이 발생한 경우 동시성 런타임 함수는 C++ 재배포 가능 패키지에 추가된 concrt140.dll로 이동되었습니다. 이 DLL은 `concurrency::parallel_for`와 같은 C++ 병렬 컨테이너 및 알고리즘에 대해 필요합니다. 또한 Windows XP에 조건 변수가 없기 때문에 동기화 기본 형식을 지원하기 위해 C++ 표준 라이브러리에는 Windows XP에서 이 DLL이 필요합니다.

CRT를 초기화하는 코드는 CRT 라이브러리가 정적으로 연결되었는지, 동적으로 연결되었는지, 네이티브, 관리 또는 혼합 코드인지에 따라 여러 라이브러리 중 하나입니다. 이 코드는 CRT 시작, 내부 스레드 단위 데이터 초기화 및 종료를 처리하며, 사용된 컴파일러 버전에 따라 다릅니다. 이 라이브러리는 동적으로 연결된 UCRT를 사용하는 경우에도 항상 정적으로 연결됩니다.

다음 표에는 CRT 초기화 및 종료를 구현하는 라이브러리가 나열되어 있습니다.

|라이브러리|특성|옵션|전처리기 지시문|
|-------------|---------------------|------------|-----------------------------|
|LIBCMT.lib|네이티브 CRT 시작을 코드에 정적으로 연결합니다.|**/MT**|_MT|
|libcmtd.lib|네이티브 CRT 시작의 디버그 버전을 정적으로 연결합니다. 재배포할 수 없습니다.|**/MTd**|_DEBUG, _MT|
|msvcrt.lib|DLL UCRT 및 vcruntime과 함께 사용할 네이티브 CRT 시작에 대한 정적 라이브러리입니다.|**/MD**|_MT, _DLL|
|msvcrtd.lib|DLL UCRT 및 vcruntime과 함께 사용할 네이티브 CRT 시작의 디버그 버전에 대한 정적 라이브러리입니다. 재배포할 수 없습니다.|**/MDd**|_DEBUG, _MT, _DLL|
|msvcmrt.lib|DLL UCRT 및 vcruntime과 함께 사용할 혼합된 네이티브 및 관리 CRT 시작에 대한 정적 라이브러리입니다.|**/clr**||
|msvcmrtd.lib|DLL UCRT 및 vcruntime과 함께 사용할 혼합된 네이티브 및 관리 CRT 시작의 디버그 버전에 대한 정적 라이브러리입니다. 재배포할 수 없습니다.|**/clr**||
|msvcurt.lib|**사용되지 않음** 순수 관리 CRT에 대한 정적 라이브러리입니다.|**/clr:pure**||
|msvcurtd.lib|**사용되지 않음** 순수 관리 CRT의 디버그 버전에 대한 정적 라이브러리입니다. 재배포할 수 없습니다.|**/clr:pure**||

C 런타임 라이브러리를 지정하는 컴파일러 옵션을 사용하지 않고 명령줄에서 프로그램을 연결하면 링커는 정적으로 연결된 CRT 라이브러리, 즉 libcmt.lib, libvcruntime.lib 및 libucrt.lib를 사용합니다.

정적으로 연결된 CRT를 사용하면 C 런타임 라이브러리에서 저장하는 모든 상태 정보가 해당 CRT 인스턴스의 로컬에 있게 됩니다. 예를 들어 정적으로 연결된 CRT를 사용할 때 [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)을 사용하는 경우 `strtok` 파서의 위치는 정적 CRT의 다른 인스턴스에 연결된 동일한 프로세스에 있는(그러나 다른 DLL 또는 EXE에 있는) 코드에 사용되는 `strtok` 상태와 관련이 없습니다. 반면 동적으로 연결된 CRT는 CRT에 동적으로 연결된 프로세스 내의 모든 코드에 대한 상태를 공유합니다. 이러한 함수의 더 안전한 새 버전을 사용하는 경우 이 문제는 적용되지 않습니다. 예를 들어 `strtok_s` 에서는 이 문제가 발생하지 않습니다.

정적 CRT에 연결하여 작성된 DLL에는 자체 CRT 상태가 있으므로 DLL에서 CRT에 정적으로 연결하는 것은 이로 인한 결과를 특별히 원하거나 알고 있는 경우 외에는 권장되지 않습니다. 예를 들어 자체의 정적 CRT에 연결된 DLL를 로드하는 실행 파일에서 [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) 를 호출하는 경우 DLL의 코드에서 생성되는 하드웨어 예외는 catch되지 않지만 주 실행 파일의 코드에서 생성되는 하드웨어 예외는 catch됩니다.

**/clr** 컴파일러 스위치를 사용하는 경우 코드가 정적 라이브러리인 msvcmrt.lib와 연결됩니다. 이 정적 라이브러리는 관리 코드와 네이티브 CRT 사이의 프록시를 제공합니다. 정적으로 연결된 CRT( **/MT** 또는 **/MTd** 옵션)를 **/clr**과 함께 사용할 수 없습니다. 대신 동적으로 연결된 라이브러리(**/MD** 또는 **/MDd**)를 사용하세요. 순수 관리 CRT 라이브러리는 Visual Studio 2015에서 사용되지 않으며 Visual Studio 2017에서 지원되지 않습니다.

**/clr**과 함께 CRT를 사용하는 방법에 대한 자세한 내용은 [혼합형(네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)를 참조하세요.

응용 프로그램의 디버그 버전을 빌드하려면 [_DEBUG](../c-runtime-library/debug.md) 플래그를 정의해야 하며 응용 프로그램을 이러한 라이브러리 중 하나의 디버그 버전과 연결해야 합니다. 라이브러리 파일의 디버그 버전을 사용하는 방법에 대한 자세한 내용은 참조 [CRT 디버깅 기술](/visualstudio/debugger/crt-debugging-techniques)을 참조하세요.

이 버전의 CRT는 C99 표준을 완벽하게 준수하지 않습니다. 특히 \<tgmath.h> 헤더 및 CX_LIMITED_RANGE/FP_CONTRACT pragma 매크로는 지원되지 않습니다. 표준 IO 함수에서 매개 변수 지정자의 의미와 같은 특정 요소는 기본적으로 레거시 해석을 사용합니다. /Zc 컴파일러 규칙 옵션을 사용하고 링커 옵션을 지정하여 라이브러리 규칙의 일부 측면을 제어할 수 있습니다.

## <a name="c-standard-library"></a>C++ 표준 라이브러리

|C++ 표준 라이브러리|특성|옵션|전처리기 지시문|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|다중 스레드, 정적 링크|**/MT**|_MT|
|msvcprt.lib|다중 스레드, 동적 링크(MSVCP*version*.dll에 대한 가져오기 라이브러리)|**/MD**|_MT, _DLL|
|libcpmtd.lib|다중 스레드, 정적 링크|**/MTd**|_DEBUG, _MT|
|msvcprtd.lib|다중 스레드, 동적 링크(MSVCP*version*D.DLL에 대한 가져오기 라이브러리)|**/MDd**|_DEBUG, _MT, _DLL|

프로젝트의 릴리스 버전을 작성할 때 선택한 컴파일러 옵션(다중 스레드, DLL, /clr)에 따라 기본 C 런타임 라이브러리(libcmt.lib, msvcmrt.lib, msvcrt.lib) 중 하나가 기본적으로 연결됩니다. 코드에 [C++ 표준 라이브러리 헤더 파일](../standard-library/cpp-standard-library-header-files.md) 중 하나를 포함하는 경우 컴파일 시 Visual C++에 의해 C++ 표준 라이브러리가 자동으로 연결됩니다. 예:

```cpp
#include <ios>
```

이진 호환성을 위해 단일 가져오기 라이브러리에서 둘 이상의 DLL 파일을 지정할 수 있습니다. 버전 업데이트는 새로운 라이브러리 기능을 도입하는 별도의 DLL인 *도트 라이브러리*를 도입할 수 있습니다. 예를 들어, Visual Studio 2017 버전 15.6에서는 msvcp140.dll이 지원하는 ABI를 손상시키지 않고 추가 표준 라이브러리 기능을 지원하기 위해 msvcp140_1.dll을 도입했습니다. Visual Studio 2017 버전 15.6 용 도구 집합에 포함된 msvcprt.lib 가져오기 라이브러리는 두 DLL을 모두 지원하며 이 버전의 vcredist는 두 DLL을 모두 설치합니다. 출시되면 도트 라이브러리는 고정 ABI를 가지며 이후 도트 라이브러리에 대한 종속성을 갖지 않습니다.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>응용 프로그램에서 여러 CRT 버전을 사용하는 경우 발생하는 문제

모든 실행 가능 이미지(EXE 또는 DLL)에는 고유한 정적으로 연결된 CRT가 있을 수 있거나, CRT에 동적으로 연결할 수 있습니다. 특정 이미지에 의해 정적으로 포함되거나 동적으로 로드된 CRT의 버전은 빌드한 도구 및 라이브러리 버전에 따라 다릅니다. 단일 프로세스는 여러 EXE 및 DLL 이미지를 로드할 수 있으며 각각 고유한 CRT가 있습니다. 각 해당 CRT는 다른 할당자를 사용하고, 다른 내부 구조체 레이아웃을 가지며, 다른 저장소 배열을 사용할 수 있습니다. 즉 할당된 메모리, CRT 리소스 또는 DLL 경계에서 전달된 클래스는 메모리 관리, 내부 정적 사용 또는 레이아웃 해석에 문제를 일으킬 수 있습니다. 예를 들어, 클래스가 하나의 DLL에 할당되었지만 다른 DLL에서 삭제했다면 어떤 CRT 비할당자가 사용될까요? 발생하는 오류는 감지하기 힘든 범위에서 즉각적으로 치명적인 범위까지 이를 수 있으며, 그러므로 이러한 리소스의 직접 전송은 권장되지 않습니다.

안정적이고 버전화 가능하도록 설계된 ABI(응용 프로그램 이진 인터페이스) 기술을 대신 사용하여 이러한 여러 문제를 피할 수 있습니다. DLL 내보내기 인터페이스를 디자인하여 값으로 정보를 전달하거나, 로컬에서 할당되어 호출자에게 반환되는 대신 호출자가 전달하는 메모리에 대해 작업합니다. 마샬링 기술을 사용하여 실행 가능 이미지 간에 구조화된 데이터를 복사합니다. 리소스를 로컬에서 캡슐화하고 클라이언트에 공개하는 핸들 또는 함수를 통해서만 조작을 허용합니다.

프로세스의 모든 이미지가 동적으로 로드된 동일한 버전의 CRT를 사용하는 경우에도 이러한 문제를 피할 수 있습니다. 모든 구성 요소가 동일한 DLL 버전의 CRT를 사용하도록 하려면 **/MD** 옵션을 사용하여 빌드하고, 동일한 컴파일러 도구 집합 및 속성 설정을 사용합니다.

동일한 버전의 CRT를 사용하는 경우에도, 프로그램에서 DLL 경계에서 특정 CRT 리소스(예: 파일 핸들, 로캘 및 환경 변수)를 전달하는 경우 주의해야 합니다. 관련된 문제 및 해결 방법에 대한 자세한 내용은 [DLL 경계를 넘어 CRT 개체를 전달할 때 발생할 수 있는 오류](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)를 참조하세요.


## <a name="see-also"></a>참고 항목

- [C 런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)
