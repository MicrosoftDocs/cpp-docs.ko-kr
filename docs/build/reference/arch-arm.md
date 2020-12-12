---
description: 자세한 정보:/arch (ARM)
title: /arch(ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: 885b624eb6a470d24d691641d0be63515ee76a49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179566"
---
# <a name="arch-arm"></a>/arch(ARM)

ARM에서 코드 생성 아키텍처를 지정합니다. 또한 [/arch (x86)](arch-x86.md) 및 [/arch (x64)](arch-x64.md)를 참조 하세요.

## <a name="syntax"></a>구문

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>인수

**/arch: ARMv7VE**<br/>
ARMv7VE 가상화 확장 명령을 사용하도록 설정합니다.

**/arch: VFPv4**<br/>
ARM VFPv4 명령을 사용하도록 설정합니다. 이 옵션을 지정하지 않으면 VFPv3이 기본값입니다.

## <a name="remarks"></a>설명

`_M_ARM_FP`매크로 (ARM의 경우에만)는 사용할 수 있는 (있는 경우) 및 **/arch** 컴파일러 옵션을 나타냅니다. 자세한 내용은 [Predefined Macros](../../preprocessor/predefined-macros.md)을 참조하세요.

[/Clr](clr-common-language-runtime-compilation.md) 을 사용 하 여 컴파일하는 경우 **/arch** 는 관리 되는 함수의 코드 생성에 영향을 주지 않습니다. **/arch** 는 네이티브 함수의 코드 생성에만 영향을 줍니다.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Visual Studio에서 /arch:ARMv7VE 또는 /arch:VFPv4 컴파일러 옵션을 설정하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **C/c + +** 폴더를 선택 합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에서 또는를 추가 `/arch:ARMv7VE` `/arch:VFPv4` 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/arch (최소 CPU 아키텍처)](arch-minimum-cpu-architecture.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
