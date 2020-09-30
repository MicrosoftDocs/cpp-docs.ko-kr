---
title: '방법: 리소스 만들기 (c + +)'
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: 88618a5b1184ce9774a58f575a3fbff2d5e63ba4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504431"
---
# <a name="how-to-create-resources-c"></a>방법: 리소스 만들기 (c + +)

다음을 수행 하 여 프로젝트에 대 한 리소스를 만들 수 있습니다.

- 리소스 스크립트 파일을 사용 합니다.

   > [!NOTE]
   > 이 단계는 리소스를 추가 하기 전에 필요 합니다.

- 프로젝트에 리소스를 추가 하 고 **리소스 뷰**를 사용 합니다.

- 리소스 템플릿을 사용 하 여 사용자 지정 된 리소스 만들기

## <a name="use-resource-script-files"></a>리소스 스크립트 파일 사용

프로젝트에 새 리소스를 만들고 추가 하려면 먼저 리소스 스크립트 (.rc) 파일을 만들어야 합니다.

> [!NOTE]
> Visual Studio IDE에 로드 된 기존 프로젝트에만 리소스 스크립트 파일을 추가할 수 있습니다. 리소스 템플릿 (.rct) 파일은 언제 든 지 만들 수 있지만 프로젝트 외부에 독립 실행형 리소스 스크립트를 만들 수는 없습니다.

### <a name="to-create-a-resource-script-file"></a>리소스 스크립트 파일을 만들려면

1. **솔루션 탐색기**에서 기존 프로젝트 폴더 (예: *MyProject*)에 포커스를 둡니다.

   > [!NOTE]
   > 프로젝트 폴더를 **솔루션 탐색기**의 솔루션 폴더와 혼동 하지 마세요. **솔루션** 폴더에 포커스를 두면 동일한 **새 항목 추가** 를 선택할 수 없습니다.

1. 메뉴에서 **프로젝트**  >  **새 항목 추가**로 이동 합니다.

1. **Visual C++** 폴더를 선택 하 고 오른쪽 창에서 **리소스 파일 (.rc)** 을 선택 합니다.

1. **이름** 텍스트 상자에서 리소스 스크립트 파일의 이름을 입력 하 고 **열기**를 선택 합니다.

### <a name="to-open-a-resource-script-file"></a>리소스 스크립트 파일을 열려면

프로젝트를 열지 않고도 리소스 스크립트 파일에서 리소스를 볼 수 있습니다. 스크립트 파일은 **리소스 뷰**아닌 문서 창에서 열립니다.

> [!NOTE]
> 일부 명령은 파일을 독립 실행형으로 연 경우에만 사용할 수 있습니다. 즉, 프로젝트 외부에서는 프로젝트를 먼저 로드 하지 않아도 됩니다. 예를 들어 다른 이름으로 **저장** 명령을 사용 하 여 다른 형식 또는 파일 이름으로 파일을 저장 하려면 파일을 독립 실행형으로 열어야 합니다.

- 프로젝트 외부에서 리소스 스크립트 파일을 열려면 메뉴에서 **파일**  >  **열기**로 이동 하 고 **파일**을 선택 합니다. 리소스 스크립트 파일로 이동 하 여 파일을 강조 표시 하 고 **열기**를 선택 합니다.

    > [!NOTE]
    > 리소스 편집기를 사용 하 여 리소스를 열지 않고 프로젝트의 리소스 스크립트 파일의 콘텐츠를 보려는 경우가 있을 수 있습니다. 예를 들어 리소스 파일에서 각 대화 상자를 별도로 열지 않고 모든 대화 상자에서 문자열을 검색하려고 할 수 있습니다. 리소스 파일을 텍스트 형식으로 쉽게 열어 포함 된 모든 리소스를 확인 하 고 텍스트 편집기에서 지 원하는 전역 작업을 완료할 수 있습니다.
    >
    > 리소스 스크립트 파일을 텍스트 형식으로 열려면 위 단계에서 **열기** 단추 오른쪽에 있는 드롭다운 화살표를 사용 하 고 **연결 프로그램**을 선택 합니다. **소스 코드 (텍스트) 편집기** 를 선택 하 고 **다음으로 열기** 드롭다운 목록에서 **텍스트** 를 선택 하면 **소스 코드** 편집기에서 리소스가 열립니다.

- 여러 리소스 스크립트를 열려면 열려는 각 파일 (예: *Source1* 및 *소스 2*)에 대해 위의 동일한 단계를 따릅니다. 그런 다음 두 .rc 파일이 별도의 문서 창에 열려 있으면 **창** 메뉴를 사용 하거나 파일 중 하나를 마우스 오른쪽 단추로 클릭 하 고 **새 가로 탭 그룹** 또는 **새 세로 탭 그룹**을 선택 합니다. 이제 창이 바둑판식으로 표시 되므로 동시에 볼 수 있습니다.

> [!TIP]
> **솔루션 탐색기**에서 .rc 파일을 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램** 을 선택 하 고 **소스 코드 (텍스트) 편집기**를 선택 하 여 리소스 스크립트 파일을 열 수 있습니다.

[Mfc 응용 프로그램 마법사](../mfc/reference/mfc-application-wizard.md)를 사용 하 여 WINDOWS 용 Mfc (Microsoft Foundation Class) 응용 프로그램을 빌드하는 경우 마법사는 mfc의 핵심 기능을 포함 하는 리소스 스크립트 (.rc) 파일을 포함 하는 기본적인 파일 집합을 생성 합니다. 그러나 MFC를 기반으로 하지 않는 Windows 응용 프로그램의 .rc 파일을 편집할 때는 이러한 MFC 관련 기능을 사용할 수 없습니다. 여기에는 코드 마법사, 메뉴 프롬프트 문자열, 콤보 상자 컨트롤의 목록 내용, ActiveX 컨트롤 호스팅 등이 포함 됩니다.

- 리소스 스크립트 파일이 열려 있는 상태에서 MFC 지원을 추가 하려면 **리소스 뷰**에서 resources 폴더 (예: *MFC .rc*)를 강조 표시 합니다. 그런 다음 [속성 창](/visualstudio/ide/reference/properties-window)에서 **MFC 모드** 를 **True**로 설정 합니다.

  > [!NOTE]
  > **Mfc 모드**를 설정 하는 것 외에도 .rc 파일은 mfc 프로젝트의 일부 여야 합니다. Win32 프로젝트의 .rc 파일에서 **Mfc 모드** 를 **True** 로 설정 하면 mfc 기능이 제공 되지 않습니다.

## <a name="create-resources"></a>리소스 만들기

리소스를 새 기본 리소스로 만들 수 있습니다. 즉, 템플릿을 기반으로 하지 않는 리소스 또는 템플릿 뒤의 리소스로 패턴화 됩니다.

**리소스 뷰** 창을 사용 하 여 프로젝트에 포함 된 리소스 파일을 표시할 수 있습니다. 최상위 폴더 (예: *Project1*)를 확장 하면 해당 파일 내의 리소스 종류가 표시 됩니다. 각 리소스 종류를 확장 하 여 해당 형식의 개별 리소스를 표시 합니다.

> [!TIP]
> **리소스 뷰** 창을 열려면 메뉴의 **View**  >  **다른 창**  >  **리소스 뷰** 보기로 이동 하거나 **ctrl** + **Shift** + **E**를 누릅니다.

**리소스 뷰** 창에서 마우스 오른쪽 단추를 클릭 하 여 명령의 바로 가기 메뉴를 시작 하거나 제목 표시줄을 두 번 클릭 하 여 창의 도킹을 해제 하 고 도킹을 해제할 수도 있습니다. 창의 동작을 제어 하는 명령에 대 한 제목 표시줄을 마우스 오른쪽 단추로 클릭 합니다. 자세한 내용은 [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)를 참조 하세요.

**리소스 뷰** 창에는 c + + windows 데스크톱 응용 프로그램 프로젝트에 리소스를 추가 하는 다음 속성이 포함 된 **리소스 추가** 대화 상자가 포함 되어 있습니다.

| 속성 | 설명 |
|---|---|
| **리소스 종류** | 만들려는 리소스의 종류를 지정 합니다.<br/><br/>커서 및 대화 상자 리소스 범주를 확장 하 여에 있는 추가 리소스를 표시할 수 *있습니다. \Microsoft Visual Studio \<version\> \VC\VCResourceTemplates \\<LCID \> \mfc.rct*. .Rct 파일을 추가 해야 하는 경우 여기에 배치 하거나 다른 [포함 경로](./how-to-include-resources-at-compile-time.md)를 지정 합니다. 트리 컨트롤의 최상위 수준에 표시 되는 리소스는 Visual Studio에서 제공 하는 기본 리소스입니다. .Rct 파일의 리소스는 해당 범주의 두 번째 수준에 나타납니다. 추가할 수 있는 .rct 파일의 수에는 미리 설정 된 제한이 없습니다.<br/><br/> |
| **새로 만들기** | **리소스 유형** 상자에서 선택한 유형을 기반으로 리소스를 만들고 해당 편집기에서 리소스를 엽니다.<br/><br/>예를 들어, 대화 상자 리소스를 만들면 [대화 상자 편집기](../windows/dialog-editor.md)에서 리소스를 엽니다. |
| **가져오기** | **가져오기** 대화 상자를 열어 현재 프로젝트로 가져올 리소스로 이동 합니다.<br/><br/>비트맵, 아이콘, 커서, HTML, 소리 (.)를 가져올 수 있습니다. WAV) 또는 사용자 지정 리소스 파일을 지정 합니다. |
| **Custom** | **새 사용자 지정 리소스** 대화 상자를 열고 사용자 지정 리소스를 만듭니다.<br/><br/>에는 사용자 지정 리소스 종류의 이름을 입력할 수 있는 텍스트 상자를 제공 하는 **리소스 종류** 속성도 포함 되어 있습니다. Visual C++ 종료 시 자동으로 이름을 대문자로 표시 합니다. 사용자 지정 리소스는 [이진 편집기](../windows/binary-editor.md)에서만 편집 됩니다. |

새 리소스를 만들 때 Visual C++에 고유한 이름을 할당 합니다 (예:) `IDD_Dialog1` . 연결 된 리소스 편집기 또는 [속성 창](/visualstudio/ide/reference/properties-window)에서 리소스 속성을 편집 하 여이 리소스 ID를 사용자 지정할 수 있습니다.

> [!NOTE]
> Visual Studio에서 예약 된 리소스 이름 또는 ID를 지정 하지 마세요. 예약 된 이름은 `DESIGNINFO` , `HWB` 및 이며 `TEXTINCLUDE` 예약 된 ID는 `255` 입니다.

### <a name="to-create-a-resource"></a>리소스를 만들려면

- **리소스 뷰**에서 .rc 파일을 선택 하 고 리소스 추가 **편집**을 사용 하 여  >  **Add Resource** 프로젝트에 추가할 리소스의 형식을 선택 합니다.

   > [!TIP]
   > **리소스 뷰** 에서 .rc 파일을 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴에서 **리소스 추가** 를 선택할 수도 있습니다.

- **솔루션 탐색기**에서 프로젝트 폴더를 마우스 오른쪽 단추로 클릭 하 고 추가 리소스 추가 **를 선택 하**  >  **Add Resource** 고 프로젝트에 추가할 리소스의 형식을 선택 합니다.

   > [!NOTE]
   > 프로젝트에 .rc 파일이 아직 없는 경우이 단계에서 하나를 만듭니다. 그런 다음 이 단계를 반복하여 새.rc 파일에 특정 리소스 형식을 추가할 수 있습니다.

- [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 클래스를 마우스 오른쪽 단추로 클릭 하 고 추가 리소스 추가 **를 선택 하**  >  **Add Resource** 고 프로젝트에 추가할 리소스의 형식을 선택 합니다.

- 메뉴 **프로젝트**  >  **리소스 추가**를 사용 합니다.

## <a name="use-resource-templates"></a>리소스 템플릿 사용

리소스 템플릿은 .rct 파일로 저장 한 사용자 지정 리소스입니다. 리소스 템플릿은 리소스를 만들기 위한 시작 지점으로 사용 됩니다. 리소스 템플릿은 표준 컨트롤 또는 반복 되는 요소와 같은 기능을 공유 하는 리소스 그룹 또는 추가 리소스를 개발 하는 시간을 절약 합니다. 예를 들어 여러 대화 상자에 회사 로고 아이콘과 함께 도움말 단추를 포함 하려는 경우 새 대화 상자 템플릿을 만들고 도움말 단추 및 로고를 사용 하 여 사용자 지정 합니다.

리소스 템플릿을 사용자 지정한 후에는 새 리소스 템플릿이 **리소스 추가** 대화 상자의 해당 리소스 형식 아래에 표시 되도록 템플릿 폴더 또는 포함 경로에 지정 된 위치에 변경 내용을 저장 합니다. 이제 필요에 따라 새 리소스 템플릿을 자주 사용할 수 있습니다.

> [!NOTE]
> 리소스 편집기에서 자동으로 고유한 리소스 ID를 제공합니다. 필요에 따라 [리소스 속성](./resource-editors.md) 을 수정할 수 있습니다.

> [!NOTE]
> 기본 템플릿 디렉터리의 하위 디렉터리에 언어별 템플릿 파일을 저장 합니다. 예를 들어, 영어 전용 템플릿 파일은 * \\<리소스 템플릿 디렉터리 \> \ 1033*로 이동 합니다.
>
> Visual Studio는 *FileFiles\Microsoft Visual studio \<version\> \VC\VCResourceTemplates*, *FileFiles\Microsoft VISUAL studio \<version> \VC\VCResourceTemplates \\<LCID \> * (예: 영어의 lcid 1033) 또는 [포함 경로의](./how-to-include-resources-at-compile-time.md)아무 곳에 나 새 .rct 파일을 검색 합니다. 다른 위치에 .rct 파일을 저장 하려면 해당 위치를 포함 경로에 추가 해야 합니다.

### <a name="to-create-and-use-a-resource-template"></a>리소스 템플릿을 만들고 사용 하려면

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**  >  **새 항목 추가**를 선택 합니다.

1. **템플릿:** 창에서 **리소스 템플릿 파일 (.rct)** 을 선택 합니다.

1. 새 *.rct* 파일의 이름과 위치를 입력 하 고 **열기**를 선택 합니다.

   새 *.rct* 파일이 프로젝트에 추가 되 고 **Resources** 폴더 아래 **솔루션 탐색기** 에 나타납니다.

1. *.Rct* 파일을 두 번 클릭 하 여 문서 창에서 엽니다. 리소스를 추가 하려면 문서 창에서 파일을 마우스 오른쪽 단추로 클릭 하 고 **리소스 추가**를 선택 합니다.

   추가 된 리소스를 사용자 지정 하 고 *.rct* 파일을 저장할 수 있습니다.

1. **리소스 뷰** 창에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 **리소스 추가**를 선택 합니다.

1. 리소스 옆에 있는 더하기 기호 ()를 선택 하 여 리소스 **+** 노드를 확장 하 고 해당 리소스에 사용할 수 있는 템플릿을 봅니다.

1. 사용할 템플릿을 두 번 클릭합니다.

   리소스 편집기에서 필요에 따라 추가 된 리소스를 수정할 수 있습니다.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>기존 리소스 파일을 템플릿으로 변환 하려면

리소스 스크립트 파일을 열고 메뉴에서 **파일**다른  >  ** \<*filename*> 이름으로 저장**으로 이동 합니다. 위치를 지정 하 고 **확인**을 선택 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 파일](../windows/resource-files-visual-studio.md)<br/>
[방법: 리소스 관리](../windows/how-to-copy-resources.md)<br/>
[방법: 컴파일 타임에 리소스 포함](../windows/how-to-include-resources-at-compile-time.md)<br/>
