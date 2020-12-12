---
description: 자세히 알아보기:/NODEFAULTLIB (라이브러리 무시)
title: /NODEFAULTLIB(라이브러리 무시)
ms.date: 03/26/2019
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: 1443d7ac1e17d464baa829d8297234ae80f3b998
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196713"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB(라이브러리 무시)

> **/Nodefaultlib**[__:__*library*]

## <a name="arguments"></a>인수

*라이브러리*<br/>
링커에서 외부 참조를 확인할 때 무시 하도록 할 라이브러리입니다.

## <a name="remarks"></a>설명

/NODEFAULTLIB 옵션은 외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 하나 이상의 기본 라이브러리를 제거 하도록 링커에 지시 합니다.

기본 라이브러리에 대 한 참조가 포함 되지 않은 .obj 파일을 만들려면 [/zl (기본 라이브러리 이름 생략)](zl-omit-default-library-name.md)을 사용 합니다.

기본적으로/NODEFAULTLIB는 외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 모든 기본 라이브러리를 제거 합니다. 선택적 *library* 매개 변수를 사용 하면 외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 지정 된 라이브러리를 제거할 수 있습니다. 제외 하려는 각 라이브러리에 대해 한 개의/NODEFAULTLIB 옵션을 지정 합니다.

링커에서는 명시적으로 지정한 라이브러리에서 먼저 검색 한 다음 [/DEFAULTLIB:](defaultlib-specify-default-library.md) 옵션으로 지정 된 기본 라이브러리와 .obj 파일에 명명 된 기본 라이브러리에서 외부 정의에 대 한 참조를 확인 합니다.

/NODEFAULTLIB:*library는* 둘 다에서 동일한 *라이브러리* 이름을 지정할 때/DEFAULTLIB:*library* 를 재정의 합니다.

C 런타임 라이브러리 없이/NODEFAULTLIB를 사용 하 여 프로그램을 빌드하는 경우에는 [/entry](entry-entry-point-symbol.md) 를 사용 하 여 프로그램에서 진입점 함수를 지정 해야 할 수도 있습니다. 자세한 내용은 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)을 참조하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **입력** 속성 페이지를 선택 합니다.

1. **모든 기본 라이브러리 무시** 속성을 선택 합니다. 또는 **특정 기본 라이브러리 무시** 속성에서 무시 하려는 라이브러리의 세미콜론으로 구분 된 목록을 지정 합니다. **명령줄** 속성 페이지는 이러한 속성에 대 한 변경 내용의 영향을 보여 줍니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>를 확인합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
