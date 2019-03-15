---
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
ms.openlocfilehash: 189affe57694a8369e9cf7ac98815cc5888b69aa
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816141"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL(증분 링크)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>설명

링커에서 증분 링크를 처리하는 방법을 제어합니다.

기본적으로 링커는 증분 모드에서 실행됩니다. 기본 증분 링크를 무시하려면 /INCREMENTAL:NO를 지정합니다.

증분 링크 된 프로그램을 비-증분 방식으로 연결 된 프로그램 기능적으로 동일 합니다. 그러나 후속 증분 링크, 증분 방식으로 연결 된 실행 파일, 정적 라이브러리 또는 동적 연결 라이브러리 파일에 대비 하기 때문에:

- 보다 크면 아닌 증분 링크 된 프로그램 코드 및 데이터를 패딩 하기 때문입니다. 안쪽 여백에는 링커가 파일을 다시 만들지 않고도 함수와 데이터의 크기를 늘릴 수 있습니다.

- 함수를 새 주소로 재배치하는 것을 처리하기 위해 점프 썽크를 포함할 수 있습니다.

   > [!NOTE]
   > 최종 릴리스 빌드에 패딩이나 썽크를 포함 되지 않았다고 되도록 프로그램을 비-증분 방식으로 연결 합니다.

기본값에 상관없이 증분 링크하려면 /INCREMENTAL을 지정합니다. 이 옵션을 선택 하면 링커에서 증분 링크할 수 없는 경우 경고가 발생 하 고 프로그램을 비-증분 방식으로 연결 합니다. 특정 옵션을 사용하는 때나 특정 경우에는 /INCREMENTAL이 무시됩니다.

대부분의 프로그램은 증분 링크될 수 있습니다. 그러나 일부 변경 사항이 너무 크면 일부 옵션이 증분 링크와 호환되지 않습니다. LINK에서는 다음 옵션 중 하나가 지정되어 있으면 전체 링크를 수행합니다.

- 증분 링크를 선택하지 않은 경우(/INCREMENTAL:NO)

- /OPT:REF를 선택한 경우

- /OPT:ICF를 선택한 경우

- /OPT:LBR을 선택한 경우

- /ORDER을 선택한 경우

/ 증분 경우 암시적 [디버그/](debug-generate-debug-info.md) 지정 됩니다.

또한 LINK에서는 다음과 같은 경우에 전체 링크를 수행합니다.

- 증분 상태 파일(.ilk)이 없는 경우 이 경우 LINK에서는 후속 증분 링크에 사용할 새 .ilk 파일을 만듭니다.

- .ilk 파일에 대한 쓰기 권한이 없는 경우. (링크 무시.ilk 파일 및 링크를 비-증분 합니다.)

- .exe 또는 .dll 출력 파일이 없는 경우.

- .ilk, .exe, .dll의 타임스탬프가 변경된 경우.

- LINK 옵션이 변경된 경우. 대부분의 LINK 옵션은 각 빌드 간에 변경된 경우 전체 링크를 수행합니다.

- 개체 파일(.obj)이 추가되거나 생략된 경우.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 하세요 [Visual Studio에서 설정 c + + 컴파일러 및 빌드 속성](../working-with-project-properties.md)합니다.

1. 선택 된 **링커** 폴더입니다.

1. **일반** 속성 페이지를 클릭합니다.

1. 수정 된 **증분 링크 사용** 속성입니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
