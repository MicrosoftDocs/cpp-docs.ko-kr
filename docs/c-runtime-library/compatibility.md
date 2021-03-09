---
title: 호환성
description: 표준 C 라이브러리, POSIX, 안전한 CRT 및 스토어 앱과 함께 Microsoft CRT (유니버설 C 런타임 라이브러리)의 호환성에 대해 설명 합니다.
ms.date: 9/11/2020
ms.topic: conceptual
helpviewer_keywords:
- CRT, compatibility
- compatibility, C runtime libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: aea87c3a7b82292a5c9c45a960a5a890a1fff3fd
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514618"
---
# <a name="compatibility"></a>호환성

CRT (유니버설 C 런타임 라이브러리)는 c + + 규칙에 필요한 C 표준 라이브러리의 대부분을 지원 합니다. 특정 예외와 함께 C99 (ISO/IEC 9899:1999) 라이브러리를 구현 합니다.

- 에서 엄격한 형식 호환성 \<complex.h> .
- `aligned_alloc`-Windows 운영 체제에서 정렬 된 할당을 지원 하지 않기 때문에 구현 되지 않을 것입니다. 비표준 `_aligned_malloc` 를 대신 사용 합니다.
- `strerrorlen_s`
- 의 원자성 지원 \<stdatomic.h>
- 의 스레딩 지원 \<threads.h>

또한 C #은 POSIX. 1 (ISO/IEC 9945-1:1996, POSIX 시스템 응용 프로그램 인터페이스) C 라이브러리의 많은 하위 집합을 구현 합니다. 그러나 특정 POSIX 표준에 완전히 부합 되지 않습니다. 또한 표준에 속하지 않는 여러 Microsoft 특정 함수 및 매크로를 구현 합니다.

Microsoft Visual C++ 구현과 관련된 함수는 vcruntime 라이브러리에 있습니다.  이러한 함수는 대부분 내부에서 사용 되며 사용자 코드에서 호출할 수 없습니다. 일부는 디버깅 및 구현 호환성에 사용하도록 문서화되어 있습니다.

C++ 표준은 구현에 대한 전역 네임스페이스에 밑줄로 시작하는 이름을 예약합니다. POSIX 함수와 Microsoft 전용 런타임 라이브러리 함수는 모두 전역 네임 스페이스에 있지만 표준 C 런타임 라이브러리에는 포함 되지 않습니다. 이러한 이유로 이러한 함수의 기본 Microsoft 구현에는 선행 밑줄이 있습니다. 이식성을 위해 UCRT는 기본 이름도 지원하지만 기본 이름을 사용하는 코드를 컴파일할 때 Microsoft C++ 컴파일러가 사용 중단 경고를 실행합니다. 기본 이름만 사용 되며 함수 자체는 사용 되지 않습니다. 이 경고를 표시하지 않으려면 원래 POSIX 이름을 사용하는 코드에서 헤더를 포함하기 전에 `_CRT_NONSTDC_NO_WARNINGS` 을 정의합니다.

표준 C 라이브러리의 특정 함수에는 잘못 사용된 매개 변수 및 확인되지 않은 버퍼로 인한 안전하지 않은 사용 기록이 있습니다. 이러한 함수가 코드에서 보안 문제의 원인이 되는 경우가 많습니다. Microsoft는 매개 변수 사용을 확인 하는 이러한 함수의 더 안전한 버전 집합을 만들었습니다. 런타임에 문제가 감지 될 때 잘못 된 매개 변수 처리기를 호출 합니다.  기본적으로 Microsoft C++ 컴파일러는 더 안전한 변형을 사용할 수 있는 함수가 사용될 때 사용 중단 경고를 실행합니다. 코드를 c + +로 컴파일하는 경우 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 1로 정의 하 여 대부분의 경고를 제거할 수 있습니다. 이 매크로를 사용 하면 템플릿 오버 로드가 이식 가능한 소스 코드를 유지 하면서 보다 안전한 변형을 호출할 수 있습니다. 이 경고를 표시하지 않으려면 이러한 함수를 사용하는 코드에서 헤더를 포함하기 전에 `_CRT_SECURE_NO_WARNINGS` 를 정의합니다. 자세한 내용은 [CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md)을 참조하세요.

설명서 내에서 특정 함수에 대해 언급된 경우를 제외하고 UCRT는 Windows API와 호환됩니다.  특정 함수는 Windows 스토어 또는 유니버설 Windows 플랫폼 ([UWP](/uwp)) 앱에서 지원 되지 않습니다. 이러한 함수는 [유니버설 Windows 플랫폼 앱에서 지원 되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)에 나열 됩니다.

## <a name="related-articles"></a>관련 문서

|제목|Description|
|-----------|-----------------|
|[UWP 앱, Windows 런타임 및 C 런타임](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|세계 RT 루틴이 유니버설 Windows 앱 또는 Microsoft Store 앱과 호환 되지 않는 경우를 설명 합니다.|
|[ANSI C 규격](../c-runtime-library/ansi-c-compliance.md)|UCRT의 표준 규격 이름 지정을 설명합니다.|
|[완전](../c-runtime-library/unix.md)|프로그램을 UNIX에 이식하는 작업에 대한 지침을 제공합니다.|
|[Windows 플랫폼 (CRT)](../c-runtime-library/windows-platforms-crt.md)|CRT가 지원되는 운영 체제를 나열합니다.|
|[이전 버전과의 호환성](../c-runtime-library/backward-compatibility.md)|이전 CRT 이름을 새 CRT 이름에 매핑하는 방법을 설명합니다.|
|[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)|CRT 라이브러리 파일(.lib) 및 관련된 컴파일러 옵션에 대한 개요를 제공합니다.|
