---
description: '자세한 정보: 링커 도구 오류 LNK2038'
title: 링커 도구 오류 LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 17fa86010b4248b68234292dd909fe50f6379c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275661"
---
# <a name="linker-tools-error-lnk2038"></a>링커 도구 오류 LNK2038

> '*name*'에 대해 일치 하는 항목이 검색 됨: '*value_1*' 값이 *파일 이름. .obj* 의 '*value_2*' 값과 일치 하지 않습니다.

링커에서 기호 불일치가 검색되었습니다. 이 오류는 응용 프로그램에서 연결 하는 라이브러리 또는 기타 개체 코드를 비롯 하 여 앱의 다른 부분이 기호의 충돌 정의를 사용 함을 나타냅니다. [검색 불일치](../../preprocessor/detect-mismatch.md) pragma는 이러한 기호를 정의 하 고 충돌 하는 값을 검색 하는 데 사용 됩니다.

## <a name="possible-causes-and-solutions"></a>가능한 원인 및 해결 방법

이 오류는 프로젝트의 개체 파일이 오래된 경우에 발생할 수 있습니다. 이 오류에 대해 다른 솔루션을 시도하기 전에 개체 파일이 최신 상태이도록 깨끗한 빌드를 수행합니다.

Visual Studio는 런타임 오류 또는 기타 예기치 않은 동작을 일으킬 수 있는 호환할 수 없는 코드 링크를 방지하기 위해 다음과 같은 기호를 정의합니다.

- `_MSC_VER` 응용 프로그램 또는 라이브러리를 빌드하는 데 사용 되는 Microsoft c + + 컴파일러 (MSVC)의 주 버전 번호 및 부 버전 번호를 나타냅니다. 한 버전의 MSVC를 사용 하 여 컴파일된 코드는 주 버전 및 부 버전 번호가 다른 버전을 사용 하 여 컴파일된 코드와 호환 되지 않습니다. 자세한 내용은 `_MSC_VER` [미리 정의 된 매크로](../../preprocessor/predefined-macros.md)에서을 참조 하세요.

   사용 중인 MSVC 버전과 호환 되지 않는 라이브러리에 연결 하는 경우 호환 되는 라이브러리 버전을 얻거나 빌드할 수 없는 경우 이전 버전의 컴파일러를 사용 하 여 프로젝트를 빌드할 수 있습니다. 프로젝트의 **플랫폼 도구 집합** 속성을 이전 도구 집합으로 변경 합니다. 자세한 내용은 [방법: 대상 프레임 워크 및 플랫폼 도구 집합 수정](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)을 참조 하세요.

- `_ITERATOR_DEBUG_LEVEL` C + + 표준 라이브러리에서 사용 되는 보안 및 디버깅 기능 수준을 나타냅니다. 이러한 기능은 특정 C++ 표준 라이브러리 개체의 표현을 변경할 수 있으며, 그 결과 다른 보안 및 디버깅 기능을 사용하는 개체와 호환되지 않을 수 있습니다. 자세한 내용은 [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)을 참조하세요.

- `RuntimeLibrary` 응용 프로그램 또는 라이브러리에서 사용 되는 c + + 표준 라이브러리 및 C 런타임의 버전을 나타냅니다. C++ 표준 라이브러리 또는 C 런타임 버전 중 하나를 사용하는 코드는 다른 버전을 사용하는 코드와 호환되지 않습니다. 자세한 내용은 [/md,/mt,/LD (Run-Time 라이브러리 사용)](../../build/reference/md-mt-ld-use-run-time-library.md)를 참조 하세요.

- `_PPLTASKS_WITH_WINRT`[PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 을 사용 하는 코드가 [/zw](../../build/reference/zw-windows-runtime-compilation.md) 컴파일러 옵션에 대해 다른 설정을 사용 하 여 컴파일된 개체에 연결 됨을 나타냅니다. (**/Zw** 는 c + +/cx 지원) PPL을 사용 하거나 PPL에 의존 하는 코드는 응용 프로그램의 나머지 부분에서 사용 되는 것과 동일한 **/Zw** 설정을 사용 하 여 컴파일해야 합니다.

이러한 기호의 값이 Visual Studio 솔루션의 프로젝트 전체에서 일치하고 응용 프로그램이 링크되는 코드 및 라이브러리와도 일치하는지 확인합니다.

## <a name="third-party-library-issues-and-vcpkg"></a>타사 라이브러리 문제 및 vcpkg

빌드의 일부로 타사 라이브러리를 구성 하려고 할 때이 오류가 표시 되는 경우 c + + 패키지 관리자 인 [vcpkg](../../build/vcpkg.md)을 사용 하 여 라이브러리를 설치 하 고 빌드합니다. vcpkg는 크고 증가 하는 [타사 라이브러리 목록을](https://github.com/Microsoft/vcpkg/tree/master/ports)지원 하 고 프로젝트의 일부로 성공한 빌드에 필요한 모든 구성 속성 및 종속성을 설정 합니다.

## <a name="see-also"></a>참고 항목

[링커 도구 오류 및 경고](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
