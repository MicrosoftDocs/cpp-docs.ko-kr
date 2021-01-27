---
description: /Zp(구조체 멤버 맞춤)에 대한 자세한 정보
title: /Zp(구조체 멤버 맞춤)
ms.date: 01/08/2021
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: 8d29c442726aff9503a42378fce6a7b8b09526ed
ms.sourcegitcommit: 14d6ae0d527d05d153e26463d4cd5ada0f43e864
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98104780"
---
# <a name="zp-struct-member-alignment"></a>/Zp(구조체 멤버 맞춤)

구조체의 멤버를 메모리에 압축하는 방법을 제어하고 모듈의 모든 구조에 대해 동일한 압축을 지정합니다.

## <a name="syntax"></a>Syntax

> **`/Zp`**[**`1`**|**`2`**|**`4`**|**`8`**|**`16`**]

## <a name="remarks"></a>설명

**`/ZpN`** 옵션은 각 구조체 멤버를 저장할 위치를 컴파일러에 알립니다. 컴파일러는 멤버 유형의 크기나 *N* 바이트 경계 중 더 작은 경계에서 첫 번째 멤버 다음의 멤버를 저장합니다.

사용할 수 있는 압축 값은 다음 표에 설명되어 있습니다.

|/Zp 인수|효과|
|-|-|
|1|1바이트 경계에서 구조체를 압축합니다. **`/Zp`** 와 같습니다.|
|2|2바이트 경계에서 구조체를 압축합니다.|
|4|4바이트 경계에서 구조체를 압축합니다.|
|8|8바이트 경계에서 구조체를 압축합니다(x86, ARM, ARM64의 경우 기본값).|
|16| 16바이트 경계에서 구조체를 압축합니다(x64의 경우 기본값).|

특정 맞춤 요구 사항이 있는 경우가 아니면 이 옵션을 사용하지 마세요.

> [!WARNING]
> Windows SDK의 C/C++ 헤더는 내부적으로 **`/Zp8`** 압축을 가정합니다. 명령줄에서 **`/Zp`** 를 사용하거나 `#pragma pack`을 사용하여 Windows SDK 헤더를 포함하는 경우 기본값에서 설정을 변경하지 마세요. 변경하는 경우 애플리케이션에서 런타임에 메모리 손상이 발생할 수 있습니다.

[`pack` pragma](../../preprocessor/pack.md)를 사용하여 구조체 압축을 제어할 수도 있습니다. 정렬에 대한 자세한 내용은 다음을 참조하십시오.

- [`align`](../../cpp/align-cpp.md)

- [`alignof` 연산자](../../cpp/alignof-operator.md)

- [`__unaligned`](../../cpp/unaligned.md)

- [`/ALIGN`(섹션 맞춤)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/C++**  > **코드 생성** 속성 페이지를 선택합니다.

1. **구조체 멤버 맞춤** 속성을 수정합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md) \
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
