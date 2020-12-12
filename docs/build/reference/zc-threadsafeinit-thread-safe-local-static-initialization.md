---
description: '자세한 정보:/Zc: threadSafeInit (스레드로부터 안전한 로컬 정적 초기화)'
title: '/Zc: threadSafeInit (스레드로부터 안전한 로컬 정적 초기화)'
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: ac14e7979d2adab0b21229f426e00a489c14f38f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271215"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc: threadSafeInit (스레드로부터 안전한 로컬 정적 초기화)

**/Zc: threadSafeInit** 컴파일러 옵션을 통해 컴파일러는 스레드로부터 안전한 방식으로 정적 로컬 (함수 범위) 변수를 초기화 하 여 수동 동기화의 필요성을 없앨 수 있습니다. 초기화만 스레드로부터 안전 합니다. 여러 스레드에서 정적 지역 변수를 사용 하 고 수정 하는 작업은 여전히 수동으로 동기화 해야 합니다. 이 옵션은 Visual Studio 2015부터 사용할 수 있습니다. 기본적으로 Visual Studio는이 옵션을 사용 하도록 설정 합니다.

## <a name="syntax"></a>Syntax

> **/Zc: threadSafeInit**[ **-** ]

## <a name="remarks"></a>설명

C + + 11 표준에서는 정적 또는 스레드 저장 기간이 있는 블록 범위 변수를 0으로 초기화 해야 다른 초기화가 수행 됩니다. 초기화는 먼저 컨트롤이 변수 선언을 통과할 때 발생 합니다. 초기화 하는 동안 예외가 throw 되는 경우 변수는 초기화 되지 않은 것으로 간주 되 고 다음 번 제어가 선언을 통해 전달 될 때 초기화가 다시 시도 됩니다. 초기화를 사용 하 여 컨트롤을 동시에 실행 하는 경우 초기화가 완료 되는 동안 동시 실행 블록이 발생 합니다. 초기화 하는 동안 제어가 재귀적으로 선언을 다시 입력 하면 동작이 정의 되지 않습니다. 기본적으로 visual studio 2015부터 Visual Studio는이 표준 동작을 구현 합니다. 이 동작은 **/zc: threadSafeInit** 컴파일러 옵션을 설정 하 여 명시적으로 지정할 수 있습니다.

**/Zc: threadSafeInit** 컴파일러 옵션은 기본적으로 설정 되어 있습니다. [/Permissive-](permissive-standards-conformance.md) 옵션은 **/Zc: threadsafeinit** 에 영향을 주지 않습니다.

정적 지역 변수를 스레드로부터 안전 하 게 초기화 하는 것은 범용 C (C 런타임 라이브러리)에서 구현 된 코드를 기반으로 합니다. Visual Studio 2015 이전의 Visual Studio 버전의 스레드로부터 안전 하지 않은 초기화 동작을 유지 하거나 Visual Studio 이전의 Visual studio 버전에 대 한 종속성을 유지 하지 않으려면 **/zc: threadSafeInit-** 옵션을 사용 합니다. 스레드로부터 안전 하지 않아도 되는 경우이 옵션을 사용 하 여 정적 로컬 선언에 대해 약간 더 작고 더 빠른 코드를 생성 합니다.

스레드로부터 안전한 정적 지역 변수는 내부적으로 TLS (스레드 로컬 저장소)를 사용 하 여 정적이 이미 초기화 된 경우 효율적인 실행을 제공 합니다. 이 기능의 구현은 Windows Vista 이상 운영 체제의 Windows 운영 체제 지원 기능에 의존 합니다. Windows XP, Windows Server 2003 및 이전 운영 체제에는이 기능이 지원 되지 않으므로 효율성 이점이 없습니다. 이러한 운영 체제는 로드 될 수 있는 TLS 섹션 수에 대 한 제한이 더 낮습니다. TLS 섹션 제한을 초과 하면 충돌이 발생할 수 있습니다. 코드에서 특히 이전 운영 체제에서 실행 해야 하는 코드에서 문제가 발생 하는 경우에는 **/zc: threadSafeInit** 를 사용 하 여 스레드로부터 안전한 초기화 코드를 사용 하지 않도록 설정 합니다.

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운 메뉴에서 **모든 구성** 을 선택 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **/Zc: threadsafeinit** 또는 **/Zc: threadsafeinit** 를 포함 하도록 **추가 옵션** 속성을 수정한 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/Zc(규칙)](zc-conformance.md)<br/>
