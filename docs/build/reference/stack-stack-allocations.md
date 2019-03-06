---
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
ms.openlocfilehash: 34d764f88b1dccb60c7d9a006be119e3800ac2d9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412772"
---
# <a name="stack-stack-allocations"></a>/STACK(스택 할당)

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>설명

/STACK 옵션 스택의 크기를 바이트 단위로 설정 합니다. .Exe 파일을 작성 하는 경우에이 옵션을 사용 합니다.

`reserve` 값 가상 메모리의 총 스택 할당을 지정 합니다. 에 대 한 ARM, x86 및 x64 컴퓨터를 기본 스택 크기는 1MB입니다.

`commit` 운영 체제에 의해 해석 될 수 있습니다. Windows WindowsRT에서는 한 번에 할당할 실제 메모리의 양을 지정합니다. 커밋된 가상 메모리 페이징 파일에 예약 될 공간을 하면 됩니다. 응용 프로그램에 더 많은 스택 공간이 필요할 때 `commit` 값이 크면 시간을 줄일 수 있지만 메모리 요구 사항이 늘어나고 시작 시간이 오래 걸릴 수 있습니다. ARM, x86 및 x64 컴퓨터를 기본 커밋 값은 4KB입니다.

10진수 또는 C 언어 표기법으로 `reserve` 및 `commit` 값을 지정합니다.

스택 크기를 설정 하는 또 다른 방법은 된 합니다 [STACKSIZE](../../build/reference/stacksize.md) 모듈 정의 (.def) 파일의 문입니다. **STACKSIZE** 스택 할당을 재정의 합니다. (/stack) 모두 지정 된 옵션입니다. .Exe 파일을 사용 하 여 빌드된 후에 스택 크기를 변경할 수는 [EDITBIN](../../build/reference/editbin-reference.md) 도구입니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 하세요 [Visual c + + 프로젝트 속성 설정](../../ide/working-with-project-properties.md)합니다.

1. 선택 된 **링커** 폴더입니다.

1. 선택 된 **시스템** 속성 페이지.

1. 다음 속성 중 하나를 수정 합니다.

   - **스택 커밋 크기**

   - **스택 예약 크기**

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. 
  <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> 속성을 참조하십시오.

## <a name="see-also"></a>참고자료

[링커 옵션 설정](../../build/reference/setting-linker-options.md)<br/>
[링커 옵션](../../build/reference/linker-options.md)
