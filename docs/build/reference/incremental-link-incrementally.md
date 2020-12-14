---
description: 자세히 알아보기:/INCREMENTAL (증분 링크)
title: /INCREMENTAL(증분 링크)
ms.date: 11/04/2016
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
ms.openlocfilehash: 4b115bd88bed5b012c29c3d0e61d471aa869b78a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191292"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL(증분 링크)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>설명

링커에서 증분 링크를 처리하는 방법을 제어합니다.

기본적으로 링커는 증분 모드에서 실행됩니다. 기본 증분 링크를 무시하려면 /INCREMENTAL:NO를 지정합니다.

증분 링크 된 프로그램은 비 증분 링크 된 프로그램과 기능적으로 동일 합니다. 그러나 후속 증분 링크에 대해 준비 되기 때문에 증분 링크 된 실행 파일, 정적 라이브러리 또는 동적 연결 라이브러리 파일은 다음과 같습니다.

- 는 코드 및 데이터의 패딩 때문에 증분 링크 되지 않은 프로그램 보다 큽니다. 패딩 기능을 사용 하면 파일을 다시 만들지 않고도 함수 및 데이터의 크기를 늘릴 수 있습니다.

- 함수를 새 주소로 재배치하는 것을 처리하기 위해 점프 썽크를 포함할 수 있습니다.

   > [!NOTE]
   > 최종 릴리스 빌드에 패딩 또는 썽크를 포함 하지 않도록 하려면 프로그램을 증분 방식으로 연결 합니다.

기본값에 상관없이 증분 링크하려면 /INCREMENTAL을 지정합니다. 이 옵션을 선택 하면 링커가 증분 링크할 수 없는 경우 경고를 발생 한 다음,이 프로그램을 증분 방식으로 연결 합니다. 특정 옵션을 사용하는 때나 특정 경우에는 /INCREMENTAL이 무시됩니다.

대부분의 프로그램은 증분 링크될 수 있습니다. 그러나 일부 변경 사항이 너무 크면 일부 옵션이 증분 링크와 호환되지 않습니다. LINK에서는 다음 옵션 중 하나가 지정되어 있으면 전체 링크를 수행합니다.

- 증분 링크를 선택하지 않은 경우(/INCREMENTAL:NO)

- /OPT:REF를 선택한 경우

- /OPT:ICF를 선택한 경우

- /OPT:LBR을 선택한 경우

- /ORDER을 선택한 경우

[/Debug](debug-generate-debug-info.md) 를 지정 하면/INCREMENTAL가 암시 됩니다.

또한 LINK에서는 다음과 같은 경우에 전체 링크를 수행합니다.

- 증분 상태 파일(.ilk)이 없는 경우 이 경우 LINK에서는 후속 증분 링크에 사용할 새 .ilk 파일을 만듭니다.

- .ilk 파일에 대한 쓰기 권한이 없는 경우. (링크는 .ilk 파일 및 비 증분 링크를 무시 합니다.)

- .exe 또는 .dll 출력 파일이 없는 경우.

- .ilk, .exe, .dll의 타임스탬프가 변경된 경우.

- LINK 옵션이 변경된 경우. 대부분의 LINK 옵션은 각 빌드 간에 변경된 경우 전체 링크를 수행합니다.

- 개체 파일(.obj)이 추가되거나 생략된 경우.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **일반** 속성 페이지를 클릭합니다.

1. **증분 링크 사용** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
