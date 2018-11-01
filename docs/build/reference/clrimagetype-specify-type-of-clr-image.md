---
title: /CLRIMAGETYPE(CLR 이미지 형식 지정)
ms.date: 11/04/2016
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: c4cdb9a9ac3376762d6aa40fd4c13abbdc7b5487
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461635"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE(CLR 이미지 형식 지정)

연결된 된 이미지의 CLR 이미지 형식을 설정 합니다.

## <a name="syntax"></a>구문

> **/CLRIMAGETYPE:**{0}**IJW**|**순수형**|**안전**|**은 SAFE32BITPREFERRED**}

## <a name="remarks"></a>설명

링커에서 네이티브 개체 및 MSIL 개체를 사용 하 여 컴파일되는 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)합니다. 합니다 **/clr: pure** 및 **/clr: safe** 컴파일러 옵션을 Visual Studio 2015에서 사용 되지 않는 및 Visual Studio 2017에서 지원 되지 않습니다. 동일한 빌드에서 혼합된 개체가 전달될 경우, 기본적으로 결과 출력 파일의 검증 가능성은 입력 모듈의 가장 낮은 검증 가능성 수준과 동일합니다. 예를 들어 네이티브 이미지 및 혼합된 모드 이미지를 전달 하는 경우 (사용 하 여 컴파일된 **/clr**), 결과 이미지는 혼합된 모드 이미지 여야 합니다.

사용할 수 있습니다 **/CLRIMAGETYPE** 필요한 경우 더 낮은 수준의 검증 가능성을 지정 합니다.

파일의 CLR 이미지 형식을 결정하는 방법에 대한 자세한 내용은 [/CLRHEADER](../../build/reference/clrheader.md)를 참조하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **구성 속성** 노드를 확장합니다.

1. 확장 된 **링커** 노드.

1. 선택 된 **고급** 속성 페이지.

1. 수정 된 **CLR 이미지 형식을** 속성입니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

- [링커 옵션 설정](../../build/reference/setting-linker-options.md)
- [링커 옵션](../../build/reference/linker-options.md)
