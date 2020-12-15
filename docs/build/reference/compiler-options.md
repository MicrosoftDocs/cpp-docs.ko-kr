---
description: '자세한 정보: 컴파일러 옵션'
title: MSVC 컴파일러 옵션
ms.date: 12/14/2020
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.openlocfilehash: f89695b00be4ed67a00f947c6b76943bfa5eaf59
ms.sourcegitcommit: 48b897797b3132ae934b1d191e3870c3c2466335
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97514577"
---
# <a name="compiler-options"></a>컴파일러 옵션

cl.exe는 Microsoft c + + (MSVC) C 및 c + + 컴파일러 및 링커를 제어 하는 도구입니다. cl.exe은 Windows 용 Microsoft Visual Studio를 지 원하는 운영 체제 에서만 실행할 수 있습니다.

> [!NOTE]
> 이 도구는 Visual Studio 개발자 명령 프롬프트에서만 시작할 수 있습니다. 시스템 명령 프롬프트 또는 파일 탐색기에서는 시작할 수 없습니다. 자세한 내용은 [명령줄에서 MSVC 도구 집합 사용](../building-on-the-command-line.md)을 참조하세요.

컴파일러는 COFF (Common Object File Format) 개체 (.obj) 파일을 생성 합니다. 링커는 실행 파일 (.exe) 또는 Dll (동적 연결 라이브러리)을 생성 합니다.

모든 컴파일러 옵션은 대/소문자를 구분 합니다. 슬래시 ( `/` ) 또는 대시 () 중 하나를 사용 하 여 `-` 컴파일러 옵션을 지정할 수 있습니다.

연결 하지 않고 컴파일하려면 [/c](c-compile-without-linking.md) 옵션을 사용 합니다.

## <a name="find-a-compiler-option"></a>컴파일러 옵션 찾기

특정 컴파일러 옵션을 찾으려면 다음 목록 중 하나를 참조 하세요.

- [컴파일러 옵션 사전순 목록](compiler-options-listed-alphabetically.md)

- [컴파일러 옵션 범주별 목록](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>컴파일러 옵션 지정

각 컴파일러 옵션에 대 한 항목에서는 개발 환경에서이를 설정 하는 방법을 설명 합니다. 개발 환경 외부에서 옵션을 지정 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

- [MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)

- [CL 명령 파일](cl-command-files.md)

- [CL 환경 변수](cl-environment-variables.md)

## <a name="related-build-tools"></a>관련 빌드 도구

[MSVC 링커 옵션](linker-options.md) 은 프로그램을 빌드하는 방법에도 영향을 줍니다.

## <a name="see-also"></a>참조

[C/C++ 빌드 참조](c-cpp-building-reference.md)<br/>
[CL이 링커를 호출 합니다.](cl-invokes-the-linker.md)
