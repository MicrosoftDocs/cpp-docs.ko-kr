---
title: -Od (디버그 비활성화)) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /od
dev_langs:
- C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adfa2e2feaf44f5f29c1a16b8e68642e438095fe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703328"
---
# <a name="od-disable-debug"></a>/Od(디버그 비활성화)

프로그램에서 모든 최적화를 해제 하 고 컴파일 속도가 빨라집니다.

## <a name="syntax"></a>구문

```
/Od
```

## <a name="remarks"></a>설명

이 옵션은 기본값입니다. 때문에 **/Od** 코드 이동 하지 않습니다. 디버깅 프로세스를 간소화 합니다. 디버깅에 대 한 컴파일러 옵션에 대 한 자세한 내용은 참조 하세요. [/z7, /Zi, /ZI (디버그 정보 형식)](../../build/reference/z7-zi-zi-debug-information-format.md)합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **C/C++** 폴더를 클릭합니다.

1. 클릭 합니다 **최적화** 속성 페이지.

1. 수정 된 **최적화** 속성입니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션 (코드 최적화)](../../build/reference/o-options-optimize-code.md)
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)<br/>
[/Z7, /Zi, /ZI(디버깅 정보 형식)](../../build/reference/z7-zi-zi-debug-information-format.md)