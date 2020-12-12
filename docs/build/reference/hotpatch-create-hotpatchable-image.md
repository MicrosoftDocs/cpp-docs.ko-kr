---
description: 자세히 알아보기:/hotpatch (핫 패치 가능 이미지 만들기)
title: /hotpatch(핫 패치 가능 이미지 만들기)
ms.date: 11/12/2018
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: 2fc5fe629afcb1e721943b852c6f92351900ab7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199872"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch(핫 패치 가능 이미지 만들기)

핫 패치 가능한 이미지를 준비합니다.

## <a name="syntax"></a>구문

```
/hotpatch
```

## <a name="remarks"></a>설명

**/Hotpatch** 를 컴파일에서 사용 하면 컴파일러가 각 함수의 첫 번째 명령이 핫 패치에 필요한 2 바이트 이상 인지 확인 합니다.

이미지를 만들기 위한 준비를 완료 하려면 **/hotpatch** 를 사용 하 여 컴파일한 후 핫 패치 가능 [(Create 핫 패치 가능 image)](functionpadmin-create-hotpatchable-image.md) 를 사용 하 여 연결 해야 합니다. cl.exe의 한 호출을 사용 하 여 이미지를 컴파일 및 연결 하는 경우 **/hotpatch** 는 **/functionpadmin** 을 의미 합니다.

명령은 ARM 아키텍처에서 항상 2 바이트 이상이 고, x64 컴파일은 항상 **/hotpatch** 가 지정 된 것 처럼 처리 되므로 이러한 대상에 대해 컴파일할 때 **/hotpatch** 를 지정할 필요가 없습니다. 그러나 **/propadmin** 을 사용 하 여 핫 패치 가능 이미지를 만들려면 계속 연결 해야 합니다. **/Hotpatch** 컴파일러 옵션은 x86 컴파일에만 영향을 줍니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/c + +** 폴더를 선택 합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 추가 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
