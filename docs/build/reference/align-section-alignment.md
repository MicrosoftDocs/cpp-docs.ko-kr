---
description: 자세한 정보:/ALIGN (섹션 맞춤)
title: /ALIGN(섹션 맞춤)
ms.date: 12/29/2017
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.openlocfilehash: d8a9af473252a2eff8957c5d2b4c54c7f7c862aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187262"
---
# <a name="align-section-alignment"></a>/ALIGN(섹션 맞춤)

## <a name="syntax"></a>Syntax

> **/Align**[**:**_number_]

### <a name="arguments"></a>인수

*number*<br/>
맞춤 값 (바이트)입니다.

## <a name="remarks"></a>설명

**/Align** 옵션은 프로그램의 선형 주소 공간 내에서 각 섹션의 맞춤을 지정 합니다. *Number* 인수는 바이트 단위 이며 2의 거듭제곱 이어야 합니다. 기본값은 4K (4096)입니다. 맞춤이 잘못 된 이미지를 생성 하는 경우 링커에서 경고를 발생 시킵니다.

장치 드라이버와 같은 응용 프로그램을 작성 하는 경우를 제외 하 고는 맞춤을 수정할 필요가 없습니다.

Align 매개 변수를 사용 하 여 특정 섹션의 맞춤을 [/SECTION](section-specify-section-attributes.md) 옵션으로 수정할 수 있습니다.

지정 하는 맞춤 값은 최대 섹션 맞춤 보다 작을 수 없습니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 적용 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
