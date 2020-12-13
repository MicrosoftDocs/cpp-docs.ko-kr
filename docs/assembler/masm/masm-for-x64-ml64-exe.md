---
description: '자세한 정보: x 64 용 MASM (ml64.exe)'
title: x64용 MASM (ml64.exe)
ms.date: 12/17/2019
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 58970f65fbd98b4cbebae0a36c615cb380ec5b75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129729"
---
# <a name="masm-for-x64-ml64exe"></a>x64용 MASM (ml64.exe)

Visual Studio에는 x64 코드를 대상으로 하는 32 비트 및 64 비트의 호스팅된 버전의 Microsoft 어셈블러 (MASM)가 모두 포함 되어 있습니다. 이름이 ml64.exe x 64 어셈블러 언어를 허용 하는 어셈블러입니다. Visual Studio를 설치 하는 동안 c + + 워크 로드를 선택 하면 MASM 명령줄 도구가 설치 됩니다. MASM 도구는 별도의 다운로드로 사용할 수 없습니다. Visual Studio의 복사본을 다운로드 하 고 설치 하는 방법에 대 한 지침은 [Visual Studio 설치](/visualstudio/install/install-visual-studio)를 참조 하세요. 전체 Visual Studio IDE를 설치 하지 않고 명령줄 도구만 필요한 경우 [Visual studio 용 빌드 도구](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)를 다운로드 합니다.

MASM을 사용 하 여 명령줄에서 x64 대상에 대 한 코드를 빌드하려면 필요한 경로 및 기타 환경 변수를 설정 하는 x64 대상의 개발자 명령 프롬프트를 사용 해야 합니다. 개발자 명령 프롬프트를 시작 하는 방법에 대 한 자세한 내용은 [명령줄에서 C/c + + 코드 빌드](../../build/building-on-the-command-line.md)를 참조 하세요.

ml64.exe 명령줄 옵션에 대 한 자세한 내용은 [ML 및 ml64.exe Command-Line 참조](ml-and-ml64-command-line-reference.md)를 참조 하세요.

X64 또는 ARM 대상에는 인라인 어셈블러 또는 ASM 키워드를 사용할 수 없습니다. 인라인 어셈블러를 사용 하는 x86 코드를 x64 또는 ARM으로 이식 하려면 코드를 c + +로 변환 하거나, 컴파일러 내장 함수를 사용 하거나, 어셈블러 언어 소스 파일을 만들 수 있습니다. Microsoft c + + 컴파일러는를 사용 하는 내장 함수를 사용 하 여 (예: 권한 있는, 비트 검사/테스트, 연동 등)를 가능한 한 플랫폼 간 방식으로 사용할 수 있습니다. 사용 가능한 내장 함수에 대 한 자세한 내용은 [컴파일러 내장 함수](../../intrinsics/compiler-intrinsics.md)를 참조 하세요.

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>Visual Studio c + + 프로젝트에 어셈블러 언어 파일 추가

Visual Studio 프로젝트 시스템은 c + + 프로젝트에서 MASM을 사용 하 여 빌드된 어셈블러 언어 파일을 지원 합니다. X64를 완전히 지 원하는 MASM을 사용 하 여 x64 어셈블러 언어 소스 파일을 만들고 개체 파일에 빌드할 수 있습니다. 그런 다음 이러한 개체 파일을 x64 대상에 대해 빌드된 c + + 코드에 연결할 수 있습니다. 이 방법은 x64 인라인 어셈블러의 부족을 극복 하는 한 가지 방법입니다.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>기존 Visual Studio c + + 프로젝트에 어셈블러 언어 파일을 추가 하려면

1. **솔루션 탐색기** 에서 프로젝트를 선택합니다. 메뉴 모음에서 **프로젝트**, **사용자 지정 빌드** 를 선택 합니다.

1. **Visual C++ 빌드 사용자 지정 파일** 대화 상자에서 **masm (.targets, props)** 옆의 확인란을 선택 합니다. **확인** 을 선택 하 여 선택 내용을 저장 하 고 대화 상자를 닫습니다.

1. 메뉴 모음에서 **프로젝트**, **새 항목 추가** 를 선택 합니다.

1. **새 항목 추가** 대화 상자의 가운데 창에서 **c + + 파일 (.cpp)** 을 선택 합니다. **이름** 편집 컨트롤에서 .cpp 대신 확장명이 **.asm** 인 새 파일 이름을 입력 합니다. **추가** 를 선택 하 여 프로젝트에 파일을 추가 하 고 대화 상자를 닫습니다.

추가한 .asm 파일에 어셈블러 언어 코드를 만듭니다. 솔루션을 빌드할 때 MASM 어셈블러를 호출 하 여 .asm 파일을 개체 파일로 어셈블한 다음 프로젝트에 연결 합니다. 기호 액세스를 보다 쉽게 만들려면 `extern "C"` 어셈블러 언어 소스 파일에서 c + + 이름 데코레이션 규칙을 사용 하는 대신 c + + 소스 코드에서로 어셈블러 함수를 선언 합니다.

## <a name="ml64-specific-directives"></a>ml64.exe 지시문

X 64를 대상으로 하는 어셈블러 언어 소스 코드에서 다음과 같은 ml64.exe 지시문을 사용할 수 있습니다.

- [.ALLOCSTACK](dot-allocstack.md)

- [.ENDPROLOG](dot-endprolog.md)

- [.PUSHFRAME](dot-pushframe.md)

- [.PUSHREG](dot-pushreg.md)

- [.SAVEREG](dot-savereg.md)

- [.SAVEXMM128](dot-savexmm128.md)

- [.SETFRAME](dot-setframe.md)

또한 ml64.exe에서 사용할 수 있도록 [PROC](proc.md) 지시어가 업데이트 되었습니다.

## <a name="32-bit-address-mode-address-size-override"></a>32 비트 주소 모드 (주소 크기 재정의)

메모리 피연산자에 32 비트 레지스터가 포함 되어 있으면 MASM은 0x67 주소 크기 재정의를 내보냅니다. 예를 들어 다음 예제에서는 주소 크기 재정의를 내보냅니다.

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM은 32 비트 치환이 단독으로 메모리 피연산자로 표시 되는 경우 64 비트 주소 지정을 의도 했다고 가정 합니다. 현재 이러한 피연산자를 사용 하는 32 비트 주소 지정을 지원 하지 않습니다.

마지막으로, 다음 코드에서 보여 주는 것 처럼 메모리 피연산자 내에서 레지스터 크기를 혼합 하 여 오류를 생성 합니다.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>참고 항목

[Microsoft 매크로 어셈블러 참조](microsoft-macro-assembler-reference.md)
