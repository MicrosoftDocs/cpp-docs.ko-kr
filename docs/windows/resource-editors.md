---
title: 리소스 편집기 (c + +)
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: f854f3cc6e61e3022e784befc738bf28c1adeb6c
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765248"
---
# <a name="resource-editors-c"></a>리소스 편집기 (c + +)

리소스 편집기는 Visual Studio 프로젝트에 포함 된 리소스를 만들거나 수정 하기 위한 특수 한 환경입니다. Visual Studio 리소스 편집기는 애플리케이션 리소스를 쉽고 빠르게 만들고 수정할 수 있도록 기술 및 인터페이스를 공유합니다. 리소스 편집기를 사용하면 적절한 편집기에서 리소스를 보고 편집하며 리소스를 미리 볼 수 있습니다.

리소스를 만들거나 열면 적절한 편집기가 자동으로 열립니다.

> [!NOTE]
> 관리 되는 프로젝트는 리소스 스크립트 파일을 사용 하지 않으므로 **솔루션 탐색기**에서 리소스를 열어야 합니다. 관리 되는 프로젝트에서 리소스 파일로 작업 하려면 [이미지 편집기](../windows/image-editor-for-icons.md) 및 [바이너리 편집기](binary-editor.md) 를 사용할 수 있습니다. 편집할 관리되는 리소스는 연결된 리소스여야 합니다. Visual Studio 리소스 편집기에서는 포함된 리소스를 편집할 수 없습니다.

|사용...|편집...|
|----------------|----------------|
|[액셀러레이터 키 편집기](../windows/accelerator-editor.md)|Visual Studio c + + 프로젝트의 액셀러레이터 키 테이블입니다.|
|[바이너리 편집기](binary-editor.md)|Visual C++, Visual Basic 또는 Visual C# 프로젝트의 이진 데이터 정보 및 사용자 지정 리소스입니다.|
|[대화 상자 편집기](../windows/dialog-editor.md)|Visual Studio c + + 프로젝트의 대화 상자|
|[이미지 편집기](../windows/image-editor-for-icons.md)|Visual C++, Visual Basic 또는 Visual C# 프로젝트의 비트맵, 아이콘, 커서 및 기타 이미지 파일입니다.|
|[메뉴 편집기](../windows/menu-editor.md)|Visual Studio c + + 프로젝트의 메뉴 리소스입니다.|
|[리본 편집기](../mfc/ribbon-designer-mfc.md)|MFC 프로젝트의 리본 리소스입니다.|
|[문자열 편집기](../windows/string-editor.md)|Visual Studio c + + 프로젝트의 문자열 테이블|
|[도구 모음 편집기](../windows/toolbar-editor.md)|Visual Studio c + + 프로젝트의 도구 모음 리소스입니다. **도구 모음 편집기** 는 **이미지 편집기**의 일부입니다.|
|[버전 정보 편집기](../windows/version-information-editor.md)|Visual Studio c + + 프로젝트의 버전 정보입니다.|

> [!NOTE]
> 프로젝트에 .rc 파일이 아직 없는 경우 [방법: 리소스 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조 하세요.

## <a name="view-and-edit-resources"></a>리소스 보기 및 편집

각 리소스 종류에는 해당 리소스 종류와 관련 된 리소스 편집기가 있습니다. 연결 된 편집기를 사용 하 여 컨트롤 및 기능을 다시 정렬 하거나 크기를 조정 하거나 추가 하거나 리소스의 여러 측면을 수정할 수 있습니다. 텍스트 형식 및 이진 형식으로 리소스를 편집할 수도 있습니다. 자세한 내용은 [방법: 리소스 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조 하세요.

일부 리소스 종류는 다양 한 방법으로 가져오고 사용할 수 있는 개별 파일입니다. 여기에는 비트맵, 아이콘, 커서, 도구 모음 및 html 파일이 포함 됩니다. 이러한 리소스에는 파일 이름과 [리소스 식별자](../windows/symbols-resource-identifiers.md)가 있습니다. Win32 프로젝트의 대화 상자, 메뉴 및 문자열 테이블과 같은 다른 항목은 리소스 스크립트 (.rc) 파일 또는 리소스 템플릿 (.rct) 파일의 일부로만 존재 합니다.

프로젝트를 열지 않고 프로젝트 외부에서 리소스를 편집할 수도 있습니다. 자세한 내용은 [방법: 리소스 만들기](./how-to-create-a-resource-script-file.md)를 참조 하세요.

> [!NOTE]
> **속성** 창을 사용 하 여 리소스의 속성을 수정할 수 있습니다.

- 리소스의 속성을 편집 하려면 [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 편집 하려는 리소스를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.  그런 다음 [속성 창](/visualstudio/ide/reference/properties-window)에서 리소스의 속성을 변경 합니다.

- 리소스 속성에 대 한 변경 내용을 취소 하려면 리소스가 **리소스 뷰** 에 포커스를 갖고 있는지 확인 하 고 **편집** 메뉴에서 **실행 취소** 를 선택 합니다.

### <a name="win32-resources"></a>Win32 리소스

[리소스 뷰](how-to-create-a-resource-script-file.md#create-resources) 창에서 Win32 리소스에 액세스할 수 있습니다.

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>리소스 편집기에서 Win32 리소스를 보려면

1. 메뉴 **보기**  >  **다른 창**  >  **리소스 뷰**로 이동 합니다.

1. **리소스 뷰** 창이 맨 위 창이 아닌 경우 **리소스 뷰** 탭을 선택 하 여 맨 위로 이동 합니다.

1. **리소스 뷰**에서 보려는 리소스를 포함 하는 프로젝트의 폴더를 확장 합니다. 예를 들어 대화 상자 리소스를 보려면 **대화 상자** 폴더를 확장 합니다.

1. 리소스를 두 번 클릭 합니다 (예: **IDD_ABOUTBOX**).

   리소스가 해당 편집기에서 열립니다. 예를 들어, 대화 상자 리소스의 경우 리소스가 **대화 상자 편집기**내부에서 열립니다.

#### <a name="to-delete-an-existing-win32-resource"></a>기존 Win32 리소스를 삭제 하려면

1. **리소스 뷰**에서 리소스 종류에 대 한 노드를 확장 합니다.

1. 삭제 하려는 리소스를 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.

> [!TIP]
> .Rc 파일이 프로젝트 외부의 문서 창에 열려 있는 경우에도이 메서드를 사용할 수 있습니다.

### <a name="managed-project-resources"></a>관리 되는 프로젝트 리소스

관리 되는 프로젝트는 리소스 스크립트 파일을 사용 하지 않으므로 **솔루션 탐색기**에서 리소스를 열어야 합니다. 관리 되는 프로젝트에서 리소스 파일로 작업 하려면 [이미지 편집기](../windows/image-editor-for-icons.md) 및 [바이너리 편집기](binary-editor.md) 를 사용 합니다. 편집 하려는 관리 되는 리소스는 연결 된 리소스 여야 하며 Visual Studio 리소스 편집기는 포함 된 리소스 편집을 지원 하지 않습니다.

- 리소스 편집기에서 관리 되는 리소스를 보려면 **솔루션 탐색기**에서 *Bitmap1.bmp*와 같은 리소스를 두 번 클릭 하면 해당 편집기에서 리소스가 열립니다.

- 기존 관리 되는 리소스를 삭제 하려면 **솔루션 탐색기**에서 삭제 하려는 리소스를 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.

## <a name="preview-resources"></a>리소스 미리 보기

리소스를 미리 보면 리소스를 열지 않고도 그래픽 리소스를 볼 수 있습니다. 미리 보기는 리소스 식별자가 숫자로 변경 되기 때문에 컴파일한 후 실행 파일에도 유용 합니다. 이러한 숫자 식별자는 종종 충분 한 정보를 제공 하지 않기 때문에 리소스를 미리 보고 신속 하 게 식별할 수 있습니다.

다음 리소스 유형은 시각적 레이아웃 미리 보기를 제공 합니다. 비트맵, 대화 상자, 아이콘, 메뉴, 커서, 도구 모음

다음 리소스는 시각적 미리 보기를 제공 하지 않습니다. 액셀러레이터 키, 매니페스트, 문자열 테이블, 버전 정보

> [!NOTE]
> 리소스를 미리 보려면 Win32가 필요 합니다.

### <a name="to-preview-resources"></a>리소스를 미리 보려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources) 또는 문서 창에서 리소스 (예: **IDD_ABOUTBOX**)를 선택 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서 **속성 페이지** 단추를 선택 합니다.

   > [!TIP]
   > 바로 가기를 사용 하 여 메뉴 **보기**  >  **속성 페이지**로 이동 합니다.

   리소스의 **속성** 페이지가 열리고 해당 리소스의 미리 보기가 표시 됩니다. **위쪽** 및 **아래쪽** 화살표 키를 사용 하 여 **리소스 뷰** 또는 문서 창에서 트리 컨트롤을 탐색할 수 있습니다. **속성** 페이지는 열린 상태로 유지 되 고 포커스가 있고 미리 볼 수 있는 모든 리소스를 표시 합니다.

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참조

[리소스 파일 작업](../windows/working-with-resource-files.md)<br/>
[리소스 파일](../windows/resource-files-visual-studio.md)<br/>
[리소스 식별자 (기호)](../windows/symbols-resource-identifiers.md)<br/>
