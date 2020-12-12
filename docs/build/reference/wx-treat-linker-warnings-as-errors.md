---
description: 자세히 알아보기:/WX (링커 경고를 오류로 처리)
title: /WX(링커 경고를 오류로 처리)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: 965c48ff9c9f975350f3c1e54d8090823be8fd2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261036"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX(링커 경고를 오류로 처리)

```
/WX[:NO]
```

## <a name="remarks"></a>설명

/WX를 설정 하면 링커에서 경고가 생성 될 경우 출력 파일이 생성 되지 않습니다.

이는 컴파일러의 **/wx** 와 비슷합니다. 자세한 내용은 [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/wd,/we,/wo,/Wv,/Wx (경고 수준)](compiler-option-warning-level.md) 를 참조 하세요. 그러나 컴파일에 **/wx** 를 지정 하는 경우에도 **/wx** 가 링크 단계에 적용 됨을 의미 하지는 않습니다. 각 도구에 대해 명시적으로 **/wx** 를 지정 해야 합니다.

기본적으로 **/wx** 는 적용 되지 않습니다. 링커 경고를 오류로 처리 하려면 **/wx** 를 지정 합니다. **/Wx: NO** 는 **/wx** 를 지정 하지 않는 것과 같습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
