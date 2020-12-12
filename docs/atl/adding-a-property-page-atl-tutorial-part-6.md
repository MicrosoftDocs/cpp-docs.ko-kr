---
description: '자세히 알아보기: 속성 페이지 추가 (ATL 자습서, 6 부)'
title: 속성 페이지 추가(ATL 자습서, 6부)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: c33789919e104cc1600622dc3972a23069afe573
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166291"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>속성 페이지 추가(ATL 자습서, 6부)

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL OLE DB 공급자 마법사를 사용할 수 없습니다.

속성 페이지는 필요한 경우 공유할 수 있는 별도의 COM 개체로 구현됩니다. 이 단계에서는 다음 작업을 수행하여 컨트롤에 속성 페이지를 추가하겠습니다.

- 속성 페이지 리소스 만들기

- 속성 페이지를 만들고 관리하는 코드 추가

- 컨트롤에 속성 페이지 추가

## <a name="creating-the-property-page-resource"></a>속성 페이지 리소스 만들기

컨트롤에 속성 페이지를 추가하려면 ATL 속성 페이지 템플릿을 사용합니다.

### <a name="to-add-a-property-page"></a>속성 페이지를 추가하려면 다음을 수행합니다.

1. **솔루션 탐색기** 에서 `Polygon`을 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서   >  **새 항목** 추가를 클릭 합니다.

1. 템플릿 목록에서 **atl**  >  **atl 속성 페이지** 를 선택 하 고 **추가** 를 클릭 합니다.

1. **ATL 속성 페이지 마법사** 가 표시되면 **짧은 이름** 으로 *PolyProp* 을 입력합니다.

1. **문자열** 을 클릭하여 **문자열** 페이지를 열고 **제목** 으로 **&Polygon** 을 입력합니다.

   속성 페이지의 **제목** 은 해당 페이지의 탭에 표시되는 문자열입니다. **Doc 문자열** 은 속성 프레임에서 상태 표시줄 또는 도구 설명에 표시하는 데 사용하는 설명입니다. 표준 속성 프레임에서는 현재 이 문자열을 사용하지 않으므로, 기본 내용으로 그대로 두어도 됩니다. 지금은 **도움말 파일** 을 생성하지 않으므로 해당 텍스트 상자의 항목을 삭제합니다.

1. **마침** 을 클릭하면 속성 페이지 개체가 생성됩니다.

다음 세 개의 파일이 생성됩니다.

|파일|설명|
|----------|-----------------|
|PolyProp.h|속성 페이지를 구현하는 C++ 클래스 `CPolyProp`을 포함합니다.|
|PolyProp.cpp|PolyProp.h 파일을 포함합니다.|
|PolyProp.rgs|속성 페이지 개체를 등록하는 레지스트리 스크립트입니다.|

코드도 다음과 같이 변경됩니다.

- Polygon.cpp의 개체 항목 맵에 새 속성 페이지가 추가됩니다.

- Polygon.idl 파일에 `PolyProp` 클래스가 추가됩니다.

- 새 레지스트리 스크립트 파일인 PolyProp.rgs가 프로젝트 리소스에 추가됩니다.

- 속성 페이지의 프로젝트 리소스에 대화 상자 템플릿이 추가됩니다.

- 지정한 속성 문자열이 리소스 문자열 테이블에 추가됩니다.

이제 속성 페이지에 표시하려는 필드를 추가합니다.

### <a name="to-add-fields-to-the-property-page"></a>속성 페이지에 필드를 추가하려면 다음을 수행합니다.

1. **솔루션 탐색기** 에서 Polygon.rc 리소스 파일을 두 번 클릭합니다. **리소스 뷰** 가 열립니다.

1. **리소스 뷰** 에서 `Dialog` 노드를 확장하고 `IDD_POLYPROP`을 두 번 클릭합니다. 여기에 컨트롤을 삽입하라고 알리는 레이블을 제외하고 비어 있는 대화 상자가 표시됩니다.

1. 해당 레이블을 선택하고 **속성** 창의 **캡션** 텍스트를 변경하여 `Sides:`로 변경합니다.

1. 텍스트 크기에 맞게 레이블 상자의 크기를 조정합니다.

1. **도구 상자** 에서 레이블의 오른쪽으로 **편집 컨트롤** 을 끕니다.

1. 최종적으로, **속성** 창을 사용하여 편집 컨트롤의 **ID** 를 `IDC_SIDES`로 변경합니다.

속성 페이지 리소스를 만드는 프로세스를 완료했습니다.

## <a name="adding-code-to-create-and-manage-the-property-page"></a>속성 페이지를 만들고 관리하는 코드 추가

속성 페이지 리소스를 만들었으므로, 이제 구현 코드를 작성해야 합니다.

먼저, **적용** 단추를 누르면 `CPolyProp` 클래스에서 개체의 면 수를 설정할 수 있도록 합니다.

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>면 수를 설정하도록 Apply 함수를 수정하려면 다음을 수행합니다.

1. PolyProp.h의 `Apply` 함수를 다음 코드로 바꿉니다.

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

한 번에 둘 이상의 클라이언트를 속성 페이지에 연결할 수 있으므로, `Apply` 함수는 편집 상자에서 검색한 값을 사용하여 각 클라이언트에서 `put_Sides`를 반복적으로 호출합니다. [CComQIPtr](../atl/reference/ccomqiptr-class.md) 클래스를 사용하고 있습니다. 이 클래스는 각 개체에서 `QueryInterface`를 수행하여 `IUnknown` 인터페이스의 `m_ppUnk` 배열에 저장된 `IPolyCtl` 인터페이스를 가져옵니다.

이제 코드에서 `Sides` 속성 설정이 실제로 실행되었는지 확인합니다. 실패한 경우 코드에서 `IErrorInfo` 인터페이스의 오류 정보를 표시하는 메시지 상자가 표시됩니다. 일반적으로, 컨테이너는 `ISupportErrorInfo` 인터페이스에 대한 개체를 요청하고 `InterfaceSupportsErrorInfo`를 먼저 호출하여 개체가 오류 정보 설정을 지원하는지 확인합니다. 이 작업은 건너뛰어도 됩니다.

[CComPtr](../atl/reference/ccomptr-class.md)에서 참조 횟수 계산을 자동으로 처리하므로, 인터페이스에서 `Release`를 호출하지 않아도 됩니다. 또한 `CComBSTR`에서 BSTR 처리를 지원하므로, 최종 `SysFreeString` 호출을 수행하지 않아도 됩니다. 다양한 문자열 변환 클래스 중 하나도 사용하므로, 필요한 경우 BSTR을 변환할 수 있습니다(USES_CONVERSION 매크로가 함수의 시작 부분에 있는 이유임).

**적용** 단추가 활성화되어야 함을 나타내기 위해 속성 페이지의 변경 플래그도 설정해야 합니다. 이 동작은 사용자가 **Sides** 편집 상자의 값을 변경할 때 발생합니다.

### <a name="to-handle-the-apply-button"></a>적용 단추를 처리하려면 다음을 수행합니다.

1. **클래스 뷰** 에서 `CPolyProp`을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **속성** 을 클릭합니다.

1. **속성** 창에서 **이벤트** 아이콘을 클릭합니다.

1. 이벤트 목록에서 `IDC_SIDES` 노드를 확장합니다.

1. 을 선택 하 `EN_CHANGE` 고 오른쪽의 드롭다운 메뉴에서 **\<Add> onenno ide** 를 클릭 합니다. `OnEnChangeSides` 처리기 선언이 Polyprop.h에 추가되고, 처리기 구현이 Polyprop.cpp에 추가됩니다.

다음으로, 처리기를 수정하겠습니다.

### <a name="to-modify-the-onenchangesides-method"></a>OnEnChangeSides 메서드를 수정하려면 다음을 수행합니다.

1. Polyprop.cpp의 `OnEnChangeSides` 메서드에 다음 코드를 추가합니다(마법사를 통해 삽입된 코드 모두 삭제).

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`IDC_SIDES` 컨트롤에 대한 `EN_CHANGE` 알림과 함께 `WM_COMMAND` 메시지가 전송되면 `OnEnChangeSides`가 호출됩니다. 그런 다음, `OnEnChangeSides`에서 `SetDirty`를 호출하고 TRUE를 전달하여 현재 속성 페이지가 변경되었으며 **적용** 단추가 활성화되어야 함을 나타냅니다.

## <a name="adding-the-property-page-to-the-control"></a>컨트롤에 속성 페이지 추가

프로젝트에 여러 개의 컨트롤이 있을 수 있기 때문에 ATL 속성 페이지 템플릿과 마법사는 컨트롤에 속성 페이지를 자동으로 추가하지 않습니다. 컨트롤의 속성 맵에 항목을 추가해야 합니다.

### <a name="to-add-the-property-page"></a>속성 페이지를 추가하려면 다음을 수행합니다.

1. PolyCtl.h를 열고, 속성 맵에 다음 줄을 추가합니다.

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

이제 컨트롤의 속성 맵이 다음과 같이 표시됩니다.

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

속성 페이지의 CLSID를 사용하여 `PROP_PAGE` 매크로를 추가할 수도 있지만, 표시된 `PROP_ENTRY` 매크로를 사용하면 컨트롤을 저장할 때 `Sides` 속성 값도 저장됩니다.

매크로에 대한 세 개의 매개 변수는 속성 설명, 속성의 DISPID, 속성이 있는 속성 페이지의 CLSID입니다. 예를 들어 이 기능은 Visual Basic에 컨트롤을 로드하고 디자인 타임에 Sides 수를 설정하는 경우에 유용합니다. Sides 수가 저장되므로, Visual Basic 프로젝트를 다시 로드할 때 Sides 수가 복원됩니다.

## <a name="building-and-testing-the-control"></a>컨트롤 빌드 및 테스트

이제 컨트롤을 빌드하고 ActiveX 컨트롤 테스트 컨테이너에 삽입합니다. **테스트 컨테이너** 에서 **편집** 메뉴의 **PolyCtl 클래스 개체** 를 클릭합니다. 추가한 정보가 포함된 속성 페이지가 나타납니다.

처음에는 **적용** 단추가 비활성화되어 있습니다. **Sides** 상자에 값을 입력하기 시작하면 **적용** 단추가 활성화됩니다. 값 입력을 마쳤으면 **적용** 단추를 클릭합니다. 컨트롤 표시가 변경되고, **적용** 단추가 다시 비활성화됩니다. 잘못된 값을 입력해 봅니다. `put_Sides` 함수에서 설정한 오류 설명을 포함하는 메시지 상자가 표시됩니다.

다음으로, 웹 페이지에 컨트롤을 배치하겠습니다.

[5단계로 돌아가기](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [7단계로 이동](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>참고 항목

[자습서](../atl/active-template-library-atl-tutorial.md)
