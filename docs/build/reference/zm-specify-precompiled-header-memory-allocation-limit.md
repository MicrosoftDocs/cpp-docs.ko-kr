---
description: 에 대 한 자세한 정보:/Zm (미리 컴파일된 헤더 메모리 할당 제한 지정)
title: /Zm(미리 컴파일된 헤더 메모리 할당 제한 지정)
ms.date: 03/08/2019
f1_keywords:
- /zm
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
ms.openlocfilehash: 624d8926961d9ca3d32ef204b70683c14dc3197f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224389"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm(미리 컴파일된 헤더 메모리 할당 제한 지정)

미리 컴파일된 헤더를 생성하기 위해 컴파일러에서 할당하는 메모리의 양을 결정합니다.

## <a name="syntax"></a>구문

```
/Zmfactor
```

## <a name="arguments"></a>인수

*이용한*<br/>
미리 컴파일된 헤더를 생성하기 위해 컴파일러에서 사용하는 메모리의 양을 결정하는 배율 인수입니다.

*요소* 인수는 컴파일러 정의 작업 버퍼의 기본 크기에 대 한 백분율입니다. *Factor* 의 기본값은 100 (백분율) 이지만 더 크거나 더 작은 값을 지정할 수 있습니다.

## <a name="remarks"></a>설명

Visual Studio 2015 이전 버전에서 c + + 컴파일러는 여러 개의 불연속 힙을 사용 하 고 각각 한정 된 제한이 있었습니다. 현재 컴파일러는 필요한 만큼 전체 힙 크기 제한까지 동적으로 힙을 증가 하 고 미리 컴파일된 헤더에서 여러 주소 범위를 구성 하도록 허용 합니다. 따라서 **/zm** 컴파일러 옵션은 거의 필요 하지 않습니다.

컴파일러의 힙 공간이 부족 하 고 **/zm** 컴파일러 옵션을 사용 하는 경우 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 오류 메시지가 표시 되 면 너무 많은 메모리를 예약 했을 수 있습니다. **/Zm** 옵션을 제거 하는 것이 좋습니다.

컴파일러가 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) 오류 메시지를 내보내는 경우 함께 제공 되는 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) 메시지는 **/zm** 컴파일러 옵션을 사용 하 여 다시 컴파일할 때 사용할 *요소* 인수를 지정 합니다. 이 메시지는 미리 컴파일된 헤더에서를 사용 하는 경우에만 유효 `#pragma hdrstop` 합니다. 다른 경우에는 Windows 가상 메모리 압력 문제로 인해 발생 하는 의사 오류가 발생 하 고, **/zm** 옵션 사용에 대 한 권장 사항은 무시 해야 합니다. 대신 **/maxcpucount** 옵션을 사용 하 여 **/mp** 옵션과 함께 MSBUILD.EXE CL.EXE 하는 경우 병렬 프로세스 수를 줄이는 것이 좋습니다. 자세한 내용은 [미리 컴파일된 헤더 (PCH) 문제 및 권장 사항](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)을 참조 하세요.

다음 표에서는 기본 미리 컴파일된 헤더 버퍼의 크기를 75로 가정 하는 경우 *요소* 인수가 메모리 할당 제한에 미치는 영향을 보여 줍니다.

|*인수* 값|메모리 할당 제한|
|-----------------------|-----------------------------|
|10|7.5MB|
|100|75 M B|
|200|150 M B|
|1000|750 M B|
|2000|1500 M B|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>메모리 할당 제한을 설정하는 기타 방법

### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 /Zm 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. 탐색 창에서 **구성 속성**  >  **C/c + +**  >  **명령줄** 을 선택 합니다.

1. **추가 옵션** 상자에 **/zm** 컴파일러 옵션을 입력 합니다.

### <a name="to-set-the-zm-compiler-option-programmatically"></a>프로그래밍 방식으로 /Zm 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
