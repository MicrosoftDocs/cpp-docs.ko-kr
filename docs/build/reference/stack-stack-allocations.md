---
description: 자세히 알아보기:/STACK (스택 할당)
title: /STACK(스택 할당)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
ms.openlocfilehash: 6e74b508d8cdb2340c73360bf35272d9113a0f75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224468"
---
# <a name="stack-stack-allocations"></a>/STACK(스택 할당)

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>설명

/STACK 옵션은 스택의 크기 (바이트)를 설정 합니다. .Exe 파일을 빌드하는 경우에만이 옵션을 사용 합니다.

`reserve`값은 가상 메모리의 총 스택 할당을 지정 합니다. ARM, x86 및 x64 컴퓨터의 경우 기본 스택 크기는 1mb입니다.

`commit` 운영 체제에서 해석할 수 있습니다. Windows WindowsRT에서는 한 번에 할당할 실제 메모리의 양을 지정합니다. 커밋된 가상 메모리를 설정 하면 페이징 파일에 공간이 예약 됩니다. 애플리케이션에 더 많은 스택 공간이 필요할 때 `commit` 값이 크면 시간을 줄일 수 있지만 메모리 요구 사항이 늘어나고 시작 시간이 오래 걸릴 수 있습니다. ARM, x86 및 x64 컴퓨터의 경우 기본 커밋 값은 4kb입니다.

10진수 또는 C 언어 표기법으로 `reserve` 및 `commit` 값을 지정합니다.

스택 크기를 설정 하는 또 다른 방법은 모듈 정의 (.def) 파일의 [STACKSIZE](stacksize.md) 문을 사용 하는 것입니다. **STACKSIZE** 는 둘 다 지정 된 경우 스택 할당 (/STACK) 옵션을 재정의 합니다. [EDITBIN](editbin-reference.md) 도구를 사용 하 여 .exe 파일을 빌드한 후에 스택 크기를 변경할 수 있습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **시스템** 속성 페이지를 선택 합니다.

1. 다음 속성 중 하나를 수정 합니다.

   - **스택 커밋 크기**

   - **스택 예약 크기**

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> 속성을 참조하십시오.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
