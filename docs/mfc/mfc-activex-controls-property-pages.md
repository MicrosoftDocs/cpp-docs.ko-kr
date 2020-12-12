---
description: '자세한 정보: MFC ActiveX 컨트롤: 속성 페이지'
title: 'MFC ActiveX 컨트롤: 속성 페이지'
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: 40267857b12b2f23c07f03d0ee77b2ae8e6bf1a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206151"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 컨트롤: 속성 페이지

ActiveX 컨트롤 사용자는 속성 페이지를 사용 하 여 ActiveX 컨트롤 속성을 보고 변경할 수 있습니다. 이러한 속성은 컨트롤 속성을 보고 편집 하기 위해 사용자 지정 된 그래픽 인터페이스를 제공 하는 하나 이상의 속성 페이지를 포함 하는 컨트롤 속성 대화 상자를 호출 하 여 액세스 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

ActiveX 컨트롤 속성 페이지는 다음과 같은 두 가지 방법으로 표시 됩니다.

- 컨트롤의 속성 동사 (**OLEIVERB_PROPERTIES**)가 호출 되 면 컨트롤은 컨트롤의 속성 페이지를 포함 하는 모달 속성 대화 상자를 엽니다.

- 컨테이너는 선택한 컨트롤의 속성 페이지를 표시 하는 자체 모덜리스 대화 상자를 표시할 수 있습니다.

다음 그림에 표시 된 속성 대화 상자는 현재 속성 페이지를 표시 하기 위한 영역, 속성 페이지를 전환 하는 데 사용할 수 있는 영역, 속성 페이지 대화 상자 닫기, 변경 내용을 취소 하거나 ActiveX 컨트롤에 대 한 변경 내용을 즉시 적용 하는 등의 일반적인 작업을 수행 하는 단추 모음으로 구성 됩니다.

![Circ3 속성 대화 상자](../mfc/media/vc373i1.gif "Circ3 속성 대화 상자") <br/>
속성 대화 상자

이 문서에서는 ActiveX 컨트롤에서 속성 페이지를 사용 하는 것과 관련 된 항목을 설명 합니다. 여기에는 다음이 포함됩니다.

- [ActiveX 컨트롤에 대 한 기본 속성 페이지 구현](#_core_implementing_the_default_property_page)

- [속성 페이지에 컨트롤 추가](#_core_adding_controls_to_a_property_page)

- [DoDataExchange 함수 사용자 지정](#_core_customizing_the_dodataexchange_function)

ActiveX 컨트롤에서 속성 페이지를 사용 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [MFC ActiveX 컨트롤: 다른 사용자 지정 속성 페이지 추가](mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX 컨트롤: 스톡 속성 페이지 사용](mfc-activex-controls-using-stock-property-pages.md)

ActiveX 컨트롤이 아닌 MFC 응용 프로그램에서 속성 시트를 사용 하는 방법에 대 한 자세한 내용은 [속성 시트](property-sheets-mfc.md)를 참조 하십시오.

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a> 기본 속성 페이지 구현

ActiveX 컨트롤 마법사를 사용 하 여 컨트롤 프로젝트를 만드는 경우 ActiveX 컨트롤 마법사는 [COlePropertyPage 클래스](reference/colepropertypage-class.md)에서 파생 된 컨트롤에 대 한 기본 속성 페이지 클래스를 제공 합니다. 처음에는이 속성 페이지가 비어 있지만 대화 상자 컨트롤 또는 컨트롤 집합을 추가할 수 있습니다. ActiveX 컨트롤 마법사는 기본적으로 속성 페이지 클래스를 하나만 만들기 때문에 클래스 뷰를 사용 하 여 추가 속성 페이지 클래스 (에서 파생 `COlePropertyPage` 됨)를 만들어야 합니다. 이 절차에 대 한 자세한 내용은 [MFC ActiveX 컨트롤: 다른 사용자 지정 속성 페이지 추가](mfc-activex-controls-adding-another-custom-property-page.md)를 참조 하세요.

속성 페이지 (이 경우 기본값)를 구현 하는 과정은 세 단계로 진행 됩니다.

#### <a name="to-implement-a-property-page"></a>속성 페이지를 구현 하려면

1. `COlePropertyPage`파생 클래스를 컨트롤 프로젝트에 추가 합니다. 이 경우와 같이 ActiveX 컨트롤 마법사를 사용 하 여 프로젝트를 만든 경우 기본 속성 페이지 클래스는 이미 있습니다.

1. 대화 상자 편집기를 사용 하 여 속성 페이지 템플릿에 컨트롤을 추가 합니다.

1. `DoDataExchange`파생 클래스의 함수를 사용자 지정 `COlePropertyPage` 하 여 속성 페이지 컨트롤과 ActiveX 컨트롤 간에 값을 교환 합니다.

예를 들어 다음 절차에서는 간단한 컨트롤인 "Sample"을 사용 합니다. ActiveX 컨트롤 마법사를 사용 하 여 샘플을 만들었으며 스톡 Caption 속성만 포함 합니다.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a> 속성 페이지에 컨트롤 추가

#### <a name="to-add-controls-to-a-property-page"></a>속성 페이지에 컨트롤을 추가 하려면

1. 컨트롤 프로젝트를 연 상태에서 리소스 뷰를 엽니다.

1. **대화 상자** 디렉터리 아이콘을 두 번 클릭 합니다.

1. IDD_PROPPAGE_SAMPLE 대화 상자를 엽니다.

   ActiveX 컨트롤 마법사는 프로젝트의 이름을 대화 상자 ID의 끝에 추가 합니다 (이 경우에는 샘플).

1. 선택한 컨트롤을 도구 상자에서 대화 상자 영역으로 끌어다 놓습니다.

1. 이 예제에서는 텍스트 레이블 컨트롤 "Caption:"과 IDC_CAPTION 식별자를 사용 하는 편집 상자 컨트롤이 면 충분 합니다.

1. 도구 모음에서 **저장** 을 클릭 하 여 변경 내용을 저장 합니다.

이제 사용자 인터페이스가 수정 되었으므로 캡션 속성에 편집 상자를 연결 해야 합니다. 다음 섹션에서 함수를 편집 하 여이 작업을 수행 `CSamplePropPage::DoDataExchange` 합니다.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a> DoDataExchange 함수 사용자 지정

속성 페이지 [CWnd::D odataexchange](reference/cwnd-class.md#dodataexchange) 함수를 사용 하면 속성 페이지 값을 컨트롤의 실제 속성 값과 연결할 수 있습니다. 링크를 설정 하려면 적절 한 속성 페이지 필드를 해당 컨트롤 속성에 매핑해야 합니다.

이러한 매핑은 속성 페이지 **DDP_** 함수를 사용 하 여 구현 됩니다. **DDP_** 함수는 표준 MFC 대화 상자에서 사용 되는 **DDX_** 함수와 유사 하 게 작동 합니다. 단, 한 가지 예외가 있습니다. 멤버 변수에 대 한 참조 외에도 **DDP_** 함수는 컨트롤 속성의 이름을 사용 합니다. 다음은 `DoDataExchange` 속성 페이지의 함수에 대 한 일반적인 항목입니다.

[!code-cpp[NVC_MFC_AxUI#31](codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

이 함수는 함수를 사용 하 여 속성 페이지의 *m_caption* 멤버 변수를 캡션과 연결 합니다 `DDP_TEXT` .

속성 페이지 컨트롤을 삽입 한 후 위에 설명 된 대로 함수를 사용 하 여 속성 페이지 컨트롤, IDC_CAPTION, 실제 컨트롤 속성 캡션 사이에 링크를 설정 해야 합니다 `DDP_Text` .

확인란, 라디오 단추 및 목록 상자와 같은 다른 대화 상자 컨트롤 형식에 대해 [속성 페이지](reference/property-pages-mfc.md) 를 사용할 수 있습니다. 다음 표에서는 속성 페이지 **DDP_** 함수 및 해당 용도에 대 한 전체 집합을 나열 합니다.

### <a name="property-page-functions"></a>속성 페이지 함수

|함수 이름|이 함수를 사용 하 여 연결|
|-------------------|-------------------------------|
|`DDP_CBIndex`|컨트롤 속성이 있는 콤보 상자에서 선택한 문자열의 인덱스입니다.|
|`DDP_CBString`|컨트롤 속성이 있는 콤보 상자의 선택 된 문자열입니다. 선택한 문자열은 속성의 값과 같은 문자로 시작할 수 있지만 완전히 일치 하지 않아도 됩니다.|
|`DDP_CBStringExact`|컨트롤 속성이 있는 콤보 상자의 선택 된 문자열입니다. 선택한 문자열과 속성의 문자열 값이 정확히 일치 해야 합니다.|
|`DDP_Check`|컨트롤 속성이 있는 확인란입니다.|
|`DDP_LBIndex`|컨트롤 속성이 있는 목록 상자에서 선택한 문자열의 인덱스입니다.|
|`DDP_LBString`|컨트롤 속성이 있는 목록 상자에서 선택한 문자열입니다. 선택한 문자열은 속성의 값과 같은 문자로 시작할 수 있지만 완전히 일치 하지 않아도 됩니다.|
|`DDP_LBStringExact`|컨트롤 속성이 있는 목록 상자에서 선택한 문자열입니다. 선택한 문자열과 속성의 문자열 값이 정확히 일치 해야 합니다.|
|`DDP_Radio`|컨트롤 속성이 있는 라디오 단추입니다.|
|`DDP_Text`|컨트롤 속성이 있는 텍스트입니다.|

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[COlePropertyPage 클래스](reference/colepropertypage-class.md)
