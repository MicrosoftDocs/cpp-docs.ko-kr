---
description: 자세히 알아보기:/IMPLIB (가져오기 라이브러리 이름)
title: /IMPLIB(가져오기 라이브러리 이름 지정)
ms.date: 11/04/2016
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
ms.openlocfilehash: 2a5ea590368d1bc3abbecf38845e97a99a0d1f96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191318"
---
# <a name="implib-name-import-library"></a>/IMPLIB(가져오기 라이브러리 이름 지정)

> /IMPLIB:*파일 이름*

## <a name="parameters"></a>매개 변수

*filename*<br/>
가져오기 라이브러리의 사용자 지정 이름입니다. 기본 이름을 대체 합니다.

## <a name="remarks"></a>설명

/IMPLIB 옵션은 내보내기가 포함 된 프로그램을 빌드할 때 링크가 만드는 가져오기 라이브러리의 기본 이름을 재정의 합니다. 기본 이름은 기본 출력 파일의 기본 이름 및 확장명 .lib에서 형성 됩니다. 다음 중 하나 이상이 지정 된 경우 프로그램에 내보내기가 포함 됩니다.

- 소스 코드의 [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) 키워드

- .Def 파일의 [EXPORTS](exports.md) 문

- LINK 명령의 [/export](export-exports-a-function.md) 사양

가져오기 라이브러리를 만들지 않으면 LINK에서/IMPLIB를 무시 합니다. 내보내기가 지정 되지 않은 경우 링크는 가져오기 라이브러리를 만들지 않습니다. 빌드에 내보내기 파일을 사용 하는 경우 LINK에서는 가져오기 라이브러리가 이미 존재 하는 것으로 가정 하 고 새로 만들지 않습니다. 가져오기 라이브러리 및 내보내기 파일에 대 한 자세한 내용은 [LIB 참조](lib-reference.md)를 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **Linker** 폴더를 클릭합니다.

1. **고급** 속성 페이지를 클릭 합니다.

1. **가져오기 라이브러리** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
