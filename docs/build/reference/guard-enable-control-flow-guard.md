---
description: 자세히 알아보기:/s가드 (제어 흐름 보호 사용)
title: /guard(제어 흐름 보호 사용)
ms.date: 11/04/2016
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
ms.openlocfilehash: 65a027a845ab7ea53fbe2ef1a6ba6bcd4a3dde87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191773"
---
# <a name="guard-enable-control-flow-guard"></a>/guard(제어 흐름 보호 사용)

제어 흐름 보호 보안 검사의 컴파일러 생성을 사용하도록 설정합니다.

## <a name="syntax"></a>구문

```
/guard:cf[-]
```

## <a name="remarks"></a>설명

**/guard:cf** 옵션은 컴파일러가 컴파일 시간에 간접 호출 대상에 대한 제어 흐름을 분석한 다음 런타임에 대상을 확인하는 코드를 삽입하게 합니다. 기본적으로, **/guard:cf** 는 해제되어 있으며, 명시적으로 설정해야 합니다. 이 옵션을 명시적으로 사용하지 않도록 설정하려면 **/guard:cf-** 를 사용합니다.

**Visual Studio 2017 이상**:이 옵션은 **`switch`** 점프 테이블을 생성 하는 문에 대해 가드를 추가 합니다.

**/guard:cf** CFG(제어 흐름 보호) 옵션이 지정된 경우 컴파일러 및 링커는 추가 런타임 보안 검사를 삽입하여 코드를 손상시키려는 시도를 감지합니다. 컴파일 및 연결 중에 코드의 모든 간접 호출이 분석되어 코드를 올바르게 실행할 경우 코드가 도달할 수 있는 모든 위치를 찾습니다. 이 정보는 이진 파일의 헤더에 추가 구조로 저장됩니다. 또한 컴파일러는 코드의 모든 간접 호출 앞에 대상이 검증된 위치 중 하나인지 확인하는 검사를 삽입합니다. CFG 인식 운영 체제에서 런타임에 검사가 실패하면 운영 체제에서 프로그램을 닫습니다.

소프트웨어에 대한 일반적인 공격은 극단적인 입력이나 예기치 않은 입력 처리의 버그를 이용합니다. 정교하게 작성된 애플리케이션 입력은 실행 코드에 대한 포인터를 포함하는 위치를 덮어쓸 수 있습니다. 이 입력을 사용하여 제어 흐름을 공격자가 제어하는 코드로 리디렉션할 수 있습니다. CFG 런타임 검사는 실행 파일의 데이터 손상 버그를 수정하지 않습니다. 대신 공격자가 버그를 사용하여 임의 코드를 실행하기 어렵게 만듭니다. CFG는 코드에서 함수 진입점 이외의 위치에 대한 호출을 방지하는 완화 도구입니다. DEP(데이터 실행 방지),  [/GS](gs-buffer-security-check.md) 스택 검사, [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) 및 [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) ASLR(주소 공간 레이아웃 불규칙화)에서 코드가 익스플로잇 벡터가 될 가능성을 줄이는 방법과 유사합니다.

CFG 익스플로잇 완화 방법을 사용하는 코드를 빌드하려면 **/guard:cf** 옵션을 컴파일러와 링커 둘 다에 전달해야 합니다. 단일 `cl` 명령을 사용하여 이진 파일이 빌드된 경우 컴파일러는 옵션을 링커에 전달합니다. 컴파일 및 연결을 별도로 수행하는 경우 컴파일러 및 링커 명령 둘 다에 옵션을 설정해야 합니다. /DYNAMICBASE 링커 옵션도 필요합니다. 이진 파일에 CFG 데이터가 있는지 확인하려면 `dumpbin /headers /loadconfig` 명령을 사용합니다. CFG 사용 이진 파일의 EXE 또는 DLL 특징 목록에 `Guard` 가 있고 가드 플래그에 `CF Instrumented` 및 `FID table present`를 사용합니다.

**/guard:cf** 옵션은 [/ZI](z7-zi-zi-debug-information-format.md) (편집하며 계속하기 디버그 정보) 또는 [/clr](clr-common-language-runtime-compilation.md) (공용 언어 런타임 컴파일)과 호환되지 않습니다.

**/guard:cf** 를 사용하여 컴파일된 코드를 해당 옵션으로 컴파일되지 않은 라이브러리 및 개체 파일에 연결할 수 있습니다. **/guard:cf** 옵션을 사용하여 연결하고 CFG 인식 운영 체제에서 실행할 경우 이 코드만 CFG로 보호됩니다. 옵션 없이 컴파일된 코드는 공격을 중지하지 않으므로 컴파일하는 모든 코드에서 옵션을 사용하는 것이 좋습니다. CFG 검사를 위한 작은 런타임 비용이 있지만 컴파일러 분석에서 안전한 것으로 입증할 수 있는 간접 점프에 대한 검사를 최적화하려고 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**, **C/C++**, **코드 생성** 을 차례로 선택합니다.

1. **제어 흐름 보호** 속성을 선택합니다.

1. 드롭다운 컨트롤에서 **예** 를 선택하여 제어 흐름 보호를 사용하도록 설정하거나, **아니요** 를 선택하여 사용하지 않도록 설정합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
