---
title: -WX (링커 경고를 오류로 처리) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /WX
dev_langs:
- C++
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91f73af0c270be4452a4b556d2cb77c0d55bed33
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722594"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX(링커 경고를 오류로 처리)

```
/WX[:NO]
```

## <a name="remarks"></a>설명

/WX를 사용 하면 링커 경고를 생성 하는 경우 생성할 출력 파일이 생성 되지 않습니다.

비슷합니다 **/WX** 컴파일러 (참조 [/w, / w0, / w1, / w2, / w3, / w4, / w1, / w2, / w3, / w4, /Wall, /wd, / we, /wo, /Wv, /WX (경고 수준)](../../build/reference/compiler-option-warning-level.md) 자세한). 그러나 지정 **/WX** 컴파일에 의미 하지 않습니다에 대 한 **/WX** 도 적용 됩니다 링크 단계; 명시적으로 지정 해야 **/WX** 각 도구에 대 한 합니다.

기본적으로 **/WX** 은 적용 되지 않습니다. 링커 경고를 오류로 처리할지를 지정 **/WX**합니다. **/WX:NO** 지정 하지 않는 것과 같습니다 **/WX**합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 하세요 [Visual c + + 프로젝트 속성 설정](../../ide/working-with-project-properties.md)합니다.

1. 클릭 합니다 **링커** 폴더입니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. 에 옵션을 입력 합니다 **추가 옵션** 상자입니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[링커 옵션 설정](../../build/reference/setting-linker-options.md)<br/>
[링커 옵션](../../build/reference/linker-options.md)