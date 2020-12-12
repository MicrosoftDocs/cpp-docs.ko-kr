---
description: '자세한 정보: MFC ActiveX 컨트롤: 다른 사용자 지정 속성 페이지 추가'
title: 'MFC ActiveX 컨트롤: 다른 사용자 지정 속성 페이지 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 3802a32ed86536850e3a15ae9ce4bb53feb1ff1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203031"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 컨트롤: 다른 사용자 지정 속성 페이지 추가

경우에 따라 ActiveX 컨트롤에는 하나의 속성 페이지에 적합 한 것 보다 많은 속성이 있습니다. 이 경우 ActiveX 컨트롤에 속성 페이지를 추가 하 여 이러한 속성을 표시할 수 있습니다.

이 문서에서는 하나 이상의 속성 페이지가 이미 있는 ActiveX 컨트롤에 새 속성 페이지를 추가 하는 방법을 설명 합니다. 스톡 속성 페이지 (글꼴, 그림 또는 색)를 추가 하는 방법에 대 한 자세한 내용은 [MFC ActiveX 컨트롤: 스톡 속성 페이지 사용](mfc-activex-controls-using-stock-property-pages.md)문서를 참조 하세요.

다음 절차에서는 ActiveX 컨트롤 마법사에서 만든 샘플 ActiveX 컨트롤 프레임 워크를 사용 합니다. 따라서 클래스 이름 및 식별자는이 예제에서 고유 합니다.

ActiveX 컨트롤에서 속성 페이지를 사용 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [MFC ActiveX 컨트롤: 속성 페이지](mfc-activex-controls-property-pages.md)

- [MFC ActiveX 컨트롤: 스톡 속성 페이지 사용](mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  새 속성 페이지는 ActiveX 컨트롤 속성 페이지에 대 한 크기 표준에 부합 하는 것이 좋습니다. 스톡 그림 및 색 속성 페이지는 250x62 개 DLU (대화 상자 단위)를 측정 합니다. 표준 글꼴 속성 페이지는 250x110 Dlu입니다. ActiveX 컨트롤 마법사에서 만든 기본 속성 페이지는 250x62 DLU standard를 사용 합니다.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>프로젝트에 새 속성 페이지 템플릿을 삽입 하려면

1. 컨트롤 프로젝트를 열고 프로젝트 작업 영역에서 리소스 뷰를 엽니다.

1. 리소스 뷰를 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 열고 **리소스 추가** 를 클릭 합니다.

1. **대화 상자** 노드를 확장 하 고 **IDD_OLE_PROPPAGE_SMALL** 를 선택 합니다.

1. **새로 만들기** 를 클릭 하 여 프로젝트에 리소스를 추가 합니다.

1. 새 속성 페이지 템플릿을 선택 하 여 **속성** 창을 새로 고칩니다 ( **리소스 뷰**).

1. **ID** 속성의 새 값을 입력 합니다. 이 예제에서는 **IDD_PROPPAGE_NEWPAGE** 를 사용 합니다.

1. 도구 모음에서 **저장** 을 클릭합니다.

### <a name="to-associate-the-new-template-with-a-class"></a>새 템플릿을 클래스와 연결 하려면

1. 클래스 뷰를 엽니다.

1. 클래스 뷰를 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **클래스 추가** 를 클릭 합니다.

   그러면 [클래스 추가](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자가 열립니다.

1. **MFC 클래스** 템플릿을 두 번 클릭 합니다.

1. [MFC 클래스 마법사](reference/mfc-add-class-wizard.md)의 **클래스 이름** 상자에 새 대화 상자 클래스의 이름을 입력 합니다. (이 예제에서는 `CAddtlPropPage` )

1. 파일 이름을 변경 하려면 **변경** 을 클릭 합니다. 구현 및 헤더 파일의 이름을 입력 하거나 기본 이름을 적용 합니다.

1. **기본 클래스** 상자에서를 선택 `COlePropertyPage` 합니다.

1. 대화 상자 **ID** 상자에서 **IDD_PROPPAGE_NEWPAGE** 를 선택 합니다.

1. **마침** 을 클릭 하 여 클래스를 만듭니다.

컨트롤의 사용자가이 새 속성 페이지에 액세스할 수 있도록 하려면 컨트롤의 속성 페이지 Id 매크로 섹션 (컨트롤 구현 파일에 있음)을 다음과 같이 변경 합니다.

[!code-cpp[NVC_MFC_AxUI#32](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

BEGIN_PROPPAGEIDS 매크로 (속성 페이지 수)의 두 번째 매개 변수를 1에서 2로 늘려야 합니다.

또한 컨트롤 구현 파일 ()도 수정 해야 합니다. .CPP) 파일에 헤더를 포함 합니다. H) 새 속성 페이지 클래스의 파일입니다.

다음 단계에서는 새 속성 페이지의 유형 이름과 캡션을 제공 하는 두 개의 새 문자열 리소스를 만듭니다.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>속성 페이지에 새 문자열 리소스를 추가 하려면

1. 컨트롤 프로젝트를 연 상태에서 리소스 뷰를 엽니다.

1. **문자열 테이블** 폴더를 두 번 클릭 한 다음 문자열을 추가 하려는 기존 문자열 테이블 리소스를 두 번 클릭 합니다.

   그러면 창에 문자열 테이블이 열립니다.

1. 문자열 테이블의 끝에서 빈 줄을 선택 하 고 문자열의 텍스트 또는 캡션을 입력 합니다 (예: "추가 속성 페이지").

   그러면 **캡션** 및 **ID** 상자가 표시 된 **문자열 속성** 페이지가 열립니다. **캡션** 상자에는 입력 한 문자열이 포함 됩니다.

1. **Id** 상자에서 문자열의 id를 선택 하거나 입력 합니다. 완료 되 면 Enter 키를 누릅니다.

   이 예에서는 새 속성 페이지의 형식 이름에 **IDS_SAMPLE_ADDPAGE** 를 사용 합니다.

1. 제목에 대해 ID 및 "추가 속성 페이지"에 대해 **IDS_SAMPLE_ADDPPG_CAPTION** 를 사용 하 여 3 단계와 4 단계를 반복 합니다.

1. 안에. 새 속성 페이지 클래스의 CPP 파일 (이 예제에서는)은 `CAddtlPropPage` `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` 다음 예제와 같이 [AfxOleRegisterPropertyPageClass](reference/registering-ole-controls.md#afxoleregisterpropertypageclass)에 의해 IDS_SAMPLE_ADDPAGE 전달 되도록를 수정 합니다.

   [!code-cpp[NVC_MFC_AxUI#33](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. 다음과 `CAddtlPropPage` 같이 IDS_SAMPLE_ADDPPG_CAPTION 생성자에 전달 되도록의 생성자를 수정 합니다 `COlePropertyPage` .

   [!code-cpp[NVC_MFC_AxUI#34](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

필요한 수정 작업을 수행한 후 프로젝트를 다시 빌드하고 테스트 컨테이너를 사용 하 여 새 속성 페이지를 테스트 합니다. 테스트 컨테이너에 액세스하는 방법은 [테스트 컨테이너로 속성 및 이벤트 테스트](testing-properties-and-events-with-test-container.md) 를 참조하세요.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
