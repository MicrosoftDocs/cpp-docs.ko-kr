---
description: 자세히 알아보기:/NATVIS (PDB에 Natvis 추가)
title: /NATVIS(PDB에 Natvis 추가)
ms.date: 08/10/2017
f1_keywords:
- /natvis
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: 7703915591a59a558c8580dd64b9be22d281d784
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190525"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS(PDB에 Natvis 추가)

> /NATVIS:*파일 이름*

## <a name="parameters"></a>매개 변수

*filename*<br/>
PDB 파일에 추가할 Natvis 파일입니다. Natvis 파일의 디버거 시각화를 PDB에 포함 합니다.

## <a name="remarks"></a>설명

/NATVIS 옵션은 Natvis 파일 파일 *이름* 에 정의 된 디버거 시각화를 링크로 생성 된 PDB 파일에 포함 합니다. 이렇게 하면 디버거가 natvis 파일과 독립적으로 시각화를 표시할 수 있습니다. 여러/NATVIS 옵션을 사용 하 여 생성 된 PDB 파일에 Natvis 파일을 둘 이상 포함할 수 있습니다.

[/Debug](debug-generate-debug-info.md) 옵션을 사용 하 여 PDB 파일을 만들지 않은 경우에는 LINK가/NATVIS를 무시 합니다. Natvis 파일의 생성 및 사용에 대 한 자세한 내용은 [Visual Studio 디버거에서 네이티브 개체의 사용자 지정 뷰 만들기](/visualstudio/debugger/create-custom-views-of-native-objects)를 참조 하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더에서 **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 텍스트 상자에/NATVIS 옵션을 추가 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- 이 옵션에는 프로그래밍 방식으로 해당 하는 항목이 없습니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
