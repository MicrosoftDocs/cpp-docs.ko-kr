---
title: Visual Studio AddressSanitizer 확장 기능 라이브러리 (VCASan)
description: Vcasan의 기술 설명입니다.
ms.date: 03/02/2021
f1_keywords:
- vcasan
helpviewer_keywords:
- vcasan.lib
- vcasan
- vcasand.lib
- libvcasan.lib
- libvcasand.lib
ms.openlocfilehash: 8728fead94b5d2b4827b34f1a5461c08c821f2e7
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471188"
---
# <a name="visual-studio-addresssanitizer-extended-functionality-library-vcasan"></a>Visual Studio AddressSanitizer 확장 기능 라이브러리 (VCAsan)

*`VCAsan*.lib`* 라이브러리는 Visual Studio에서 확장 된 디버거 IDE 기능을 구현 합니다. 이러한 기능을 통해 IDE는 라이브 디버그 세션에서 AddressSanitizer 오류를 표시 하거나 메타 데이터가 포함 된 크래시 덤프 파일을 저장 하 여 오프 라인으로 표시할 수 있습니다. 라이브러리는 AddressSanitizer가 MSVC 컴파일러에 의해 활성화 될 때마다 연결 됩니다.

## <a name="vcasan-library-inventory"></a>VCAsan 라이브러리 인벤토리

| 런타임 옵션 | VCAsan 링크 라이브러리  |
|---------------|----------------------|
| **`/MT`**           | *`libvcasan.lib`*        |
| **`/MD`**           | *`vcasan.lib`*           |
| **`/MTd`**          | *`libvcasand.lib`*       |
| **`/MDd`**          | *`vcasand.lib`*          |

## <a name="vcasan-library-features"></a>VCAsan 라이브러리 기능

### <a name="rich-addresssanitizer-error-report-window-in-visual-studio-ide"></a>Visual Studio IDE의 리치 AddressSanitizer 오류 보고서 창

VCAsan 라이브러리는 인터페이스 함수를 사용 하 여 AddressSanitizer 런타임 내에 콜백을 등록 합니다 [`__asan_set_error_report_callback`](https://github.com/llvm/llvm-project/blob/1ba5ea67a30170053964a28f2f47aea4bb7f5ff1/compiler-rt/include/sanitizer/asan_interface.h#L256) . AddressSanitizer 보고서가 생성 되는 경우이 콜백은 Visual Studio에서 catch 한 예외를 throw 하는 데 사용 됩니다. Visual Studio는 예외 데이터를 사용 하 여 IDE에서 사용자에 게 표시 되는 메시지를 생성 합니다.

> [!NOTE]
> VCAsan 라이브러리는 AddressSanitizer 런타임에 콜백 함수를 등록 합니다. 코드에서이 등록 함수를 두 번 호출 하는 경우 VCAsan 라이브러리 콜백 등록을 덮어씁니다. 이로 인해 모든 Visual Studio IDE 통합이 손실 됩니다. 기본 IDE 사용자 환경으로 돌아갑니다. 또한 콜백을 등록 하는 사용자의 호출이 손실 될 수 있습니다. 문제가 발생 하는 경우 [버그](https://aka.ms/feedback/report?space=62)를 파일에 표시 합니다.

### <a name="save-addresssanitizer-errors-in-a-new-type-of-crash-dump-file"></a>새 유형의 크래시 덤프 파일에 AddressSanitizer 오류 저장

VCAsan 라이브러리를 실행 파일에 연결 하는 경우 사용자가 런타임에 크래시 덤프를 생성할 수 있도록 설정할 수 있습니다. 그러면 진단 오류가 발생할 때 AddressSanitizer 런타임에서 덤프 파일을 생성 합니다. 이 기능을 사용 하기 위해 사용자는 `ASAN_SAVE_DUMPS` 다음과 같은 명령을 사용 하 여 환경 변수를 설정 합니다.

`set ASAN_SAVE_DUMPS=MyFileName.dmp`

이 파일에는 Visual Studio IDE 규칙을 따라야 하는 .dmp 접미사가 있어야 합니다.

에 대해 덤프 파일을 지정할 때 발생 하는 작업은 `ASAN_SAVE_DUMPS` 다음과 같습니다. AddressSanitizer 런타임에서 오류가 발생 하면 오류와 연결 된 메타 데이터가 포함 된 크래시 덤프 파일을 저장 합니다. Visual Studio 버전 16.9 이상 버전의 디버거는 덤프 파일에 저장 된 메타 데이터를 구문 분석할 수 있습니다. 테스트 별로를 설정 하 고 `ASAN_SAVE_DUMPS` , 이러한 이진 아티팩트를 저장 한 다음 적절 한 소스 인덱싱을 사용 하 여 IDE에서 볼 수 있습니다.

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
