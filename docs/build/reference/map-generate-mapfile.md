---
description: 자세한 정보:/MAP (맵 파일 생성)
title: /MAP(맵파일 생성)
ms.date: 11/04/2016
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
ms.openlocfilehash: 28e3823099b4893dcf344a0b1aae99577d850821
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176433"
---
# <a name="map-generate-mapfile"></a>/MAP(맵파일 생성)

```
/MAP[:filename]
```

## <a name="arguments"></a>인수

*filename*<br/>
맵 파일의 사용자 지정 이름입니다. 기본 이름을 대체 합니다.

## <a name="remarks"></a>설명

/MAP 옵션을 통해 링커가 맵 파일을 만들도록 지시 합니다.

기본적으로 링커는 프로그램의 기본 이름 및 확장명 map을 사용 하 여 맵 파일의 이름을로 바꿉니다. 선택적 *파일 이름* 으로 맵 파일의 기본 이름을 재정의할 수 있습니다.

맵 파일은 링크 되는 프로그램에 대 한 다음 정보를 포함 하는 텍스트 파일입니다.

- 파일의 기본 이름인 모듈 이름입니다.

- 프로그램 파일 헤더의 타임 스탬프 (파일 시스템이 아님)

- 각 그룹의 시작 주소 ( *섹션*:*오프셋*), 길이, 그룹 이름 및 클래스를 포함 하는 프로그램의 그룹 목록입니다.

- 각 주소 ( *섹션*:*오프셋*), 기호 이름, 플랫 주소 및 기호가 정의 된 .obj 파일을 사용 하는 공용 기호 목록

- 진입점 ( *섹션*:*오프셋*)

[/MAPINFO](mapinfo-include-information-in-mapfile.md) 옵션은 맵 파일에 포함할 추가 정보를 지정 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **디버그** 속성 페이지를 클릭 합니다.

1. **맵 파일 생성** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>를 확인합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
