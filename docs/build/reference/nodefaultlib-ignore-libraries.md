---
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
ms.openlocfilehash: 24528eb4c387c4cd0921ab089370d72b076ad640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320521"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB(라이브러리 무시)

> **/NODEFAULTLIB**[__:__*library*]

## <a name="arguments"></a>인수

*library*<br/>
링커가 외부 참조를 확인할 때 무시 하도록 하려는 라이브러리입니다.

## <a name="remarks"></a>설명

/NODEFAULTLIB 옵션을 사용 하면 링커에서 외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 하나 이상의 기본 라이브러리를 제거 합니다.

기본 라이브러리에 대 한 참조를 포함 하는.obj 파일을 만들려면 사용 [/Zl (기본 라이브러리 이름 생략)](zl-omit-default-library-name.md)합니다.

기본적으로 /NODEFAULTLIB 외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 모든 기본 라이브러리를 제거 합니다. 선택적 *라이브러리* 매개 변수를 사용 하면 외부 참조를 확인할 때 검색 하는 라이브러리 목록에서 지정된 된 라이브러리를 제거 합니다. 제외 하려는 각 라이브러리에 대 한 한 가지 /NODEFAULTLIB 옵션을 지정 합니다.

링커는 명시적으로 지정 하 여 라이브러리 지정 하는 기본 라이브러리에서 먼저 검색 하 여 외부 정의에 대 한 참조를 확인 합니다 [/DEFAULTLIB:](defaultlib-specify-default-library.md) 옵션 다음에 라이브러리에에서 지정 된 기본.obj 및 파일입니다.

/NODEFAULTLIB:*라이브러리* /DEFAULTLIB 재정의:*라이브러리* 때 동일 *라이브러리* 둘 다에 이름을 지정 합니다.

또한 사용 하 여 할 /NODEFAULTLIB을 사용 하 여 C 런타임 라이브러리 없이 프로그램을 빌드하는 경우 [/ENTRY](entry-entry-point-symbol.md) 프로그램의 진입점 함수를 지정 합니다. 자세한 내용은 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)을 참조하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. 선택 된 **구성 속성** > **링커** > **입력** 속성 페이지.

1. 선택 된 **모든 기본 라이브러리 무시** 속성입니다. 또는에서 무시 하려는 라이브러리의 세미콜론으로 구분 된 목록을 지정 합니다 **특정 기본 라이브러리 무시** 속성입니다. 합니다 **명령줄** 속성 페이지의 이러한 속성을 변경한 결과 보여 줍니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>을 참조하십시오.

## <a name="see-also"></a>참고자료

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
