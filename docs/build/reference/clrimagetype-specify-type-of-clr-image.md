---
description: 자세히 알아보기:/CLRIMAGETYPE (CLR 이미지 형식 지정)
title: /CLRIMAGETYPE(CLR 이미지 형식 지정)
ms.date: 05/16/2019
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: 7c499eeddcacd674a9dfc2134e059fd8b3b9a6b6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179150"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE(CLR 이미지 형식 지정)

연결된 이미지에서 CLR 이미지 형식을 설정합니다.

## <a name="syntax"></a>Syntax

> **/CLRIMAGETYPE:**{**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>설명

링커는 [/clr](clr-common-language-runtime-compilation.md)을 사용하여 컴파일되는 고유 개체 및 MSIL 개체를 받아들입니다. **/clr:pure** 및 **/clr:safe** 컴파일러 옵션은 Visual Studio 2015에서는 더 이상 사용되지 않으며 Visual Studio 2017 이상에서는 지원되지 않습니다. 동일한 빌드에서 혼합된 개체가 전달될 경우, 기본적으로 결과 출력 파일의 검증 가능성은 입력 모듈의 가장 낮은 검증 가능성 수준과 동일합니다. 예를 들어, 네이티브 이미지 및 혼합 모드 이미지(**/clr** 을 사용하여 컴파일)를 전달할 경우, 결과 이미지는 혼합 모드 이미지입니다.

필요한 경우, **/CLRIMAGETYPE** 을 사용해서 낮은 수준의 검증 가능성을 지정할 수 있습니다.

파일의 CLR 이미지 형식을 결정하는 방법에 대한 자세한 내용은 [/CLRHEADER](clrheader.md)를 참조하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** 노드를 확장합니다.

1. **링커** 노드를 확장합니다.

1. **고급** 속성 페이지를 클릭합니다.

1. **CLR 이미지 형식을** 속성을 수정합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

- [MSVC 링커 참조](linking.md)
- [MSVC 링커 옵션](linker-options.md)
