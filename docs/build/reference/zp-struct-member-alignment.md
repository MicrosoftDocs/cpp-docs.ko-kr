---
description: 자세한 정보:/Zp (구조체 멤버 맞춤)
title: /Zp(구조체 멤버 맞춤)
ms.date: 04/04/2019
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
ms.openlocfilehash: b2029ebded53bcae1b44b5cd72bf59494e58ec4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224311"
---
# <a name="zp-struct-member-alignment"></a>/Zp(구조체 멤버 맞춤)

구조체의 멤버를 메모리에 압축 하 고 모듈의 모든 구조에 대해 동일한 압축을 지정 하는 방법을 제어 합니다.

## <a name="syntax"></a>Syntax

> **`/Zp`**[**`1`**|**`2`**|**`4`**|**`8`**|**`16`**]

## <a name="remarks"></a>설명

**`/ZpN`** 옵션은 각 구조체 멤버를 저장할 위치를 컴파일러에 알립니다. 컴파일러는 멤버 형식의 크기가 작은 경계 또는 *N* 바이트 경계에서 첫 번째 멤버 다음에 멤버를 저장 합니다.

사용 가능한 압축 값은 다음 표에 설명 되어 있습니다.

|/Zp 인수|효과|
|-|-|
|1|1 바이트 경계에서 구조체를 압축 합니다. **`/Zp`** 와 같습니다.|
|2|2 바이트 경계에서 구조체를 압축 합니다.|
|4|4 바이트 경계에서 구조체를 압축 합니다.|
|8|8 바이트 경계에서 구조체를 압축 합니다 (x86, ARM 및 ARM64의 경우 기본값).|
|16| 16 바이트 경계에서 구조체를 압축 합니다 (x64의 경우 기본값).|

특정 맞춤 요구 사항이 있는 경우가 아니면이 옵션을 사용 하지 마세요.

> [!WARNING]
> Windows SDK 집합의 c + + 헤더는 **`/Zp8`** 내부적으로 압축 하는 것으로 가정 합니다. **`/Zp`** Windows SDK 헤더 내에서 설정을 변경 하면 메모리 손상이 발생할 수 있습니다. 헤더는 **`/Zp`** 명령줄에서 설정 하는 옵션의 영향을 받지 않습니다.

를 사용 하 여 [`pack`](../../preprocessor/pack.md) 구조체 압축을 제어할 수도 있습니다. 정렬에 대한 자세한 내용은 다음을 참조하십시오.

- [`align`](../../cpp/align-cpp.md)

- [`alignof` 연산자](../../cpp/alignof-operator.md)

- [`__unaligned`](../../cpp/unaligned.md)

- [`/ALIGN` (섹션 맞춤)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **코드 생성** 속성 페이지를 선택 합니다.

1. **구조체 멤버 맞춤** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md) \
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
