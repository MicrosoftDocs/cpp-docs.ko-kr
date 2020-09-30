---
title: 속성 추가
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 63985643973782ea2b4240a338d66cb5cc2195dc
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504685"
---
# <a name="add-a-property"></a>속성 추가

[속성 추가 마법사](#names-add-property-wizard)를 사용하여 프로젝트의 인터페이스에 메서드를 추가할 수 있습니다.

**개체에 속성을 추가하려면:**

1. [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 속성을 추가할 인터페이스의 이름을 마우스 오른쪽 단추로 클릭합니다.

   > [!NOTE]
   > 프로젝트에 특성이 지정되지 않은 경우 라이브러리 노드 내에 중첩된 dispinterface에 속성을 추가할 수도 있습니다.

1. 바로 가기 메뉴에서 **추가**를 선택한 다음, **속성 추가**를 선택합니다.

1. [속성 추가 마법사](#names-add-property-wizard)에서 속성을 만드는 데 필요한 정보를 제공합니다.

1. 마법사의 [IDL 특성](#idl-attributes-add-property-wizard) 페이지에서 이 속성에 대한 IDL(인터페이스 정의 언어) 설정을 지정합니다.

1. **마침**을 선택하여 속성을 추가합니다.

속성의 `Get` 및 `Put` 메서드는 해당 속성이 정의된 인터페이스의 클래스 뷰에서 두 개의 아이콘으로 표시됩니다. 두 아이콘 중 하나를 두 번 클릭하여 .Idl 파일에서 속성 선언을 볼 수 있습니다.

- ATL 인터페이스의 경우 `Get` 및 `Put` 함수가 .cpp 파일에 추가되고, 이러한 함수에 대한 참조가 .h 파일에 추가됩니다.

- MFC dispinterface의 경우 구현 형식으로 **멤버 변수**를 선택하면, 메서드 및 변수가 구현 클래스에 추가됩니다. 구현 형식으로 **Get/Set 메서드**를 선택하면 이를 구현하는 클래스에 두 메서드가 추가됩니다.

## <a name="in-this-section"></a>단원 내용

- [이름, 속성 추가 마법사](#names-add-property-wizard)
- [IDL 특성, 속성 추가 마법사](#idl-attributes-add-property-wizard)
- [스톡 속성](#stock-properties)

## <a name="names-add-property-wizard"></a>이름, 속성 추가 마법사

이 마법사를 사용하여 인터페이스에 속성을 추가합니다.

- **속성 형식**

  추가하는 속성의 형식을 설정합니다. MFC dispinterface의 경우, 형식을 직접 제공하거나 미리 정의된 목록에서 선택합니다. 속성의 스톡 구현을 제공하는 경우 **속성 형식**이 스톡 형식으로 설정되고 변경할 수 없습니다.

- **속성 이름**

  속성 이름을 설정합니다. ActiveX 컨트롤과 연결된 MFC dispinterface의 경우, 사용자 고유의 이름을 제공하거나 미리 정의된 목록에서 스톡 속성 이름을 선택할 수 있습니다. 고유한 속성 이름을 제공하는 경우 **스톡** 구현 형식을 사용할 수 없습니다. 목록의 속성에 대한 설명은 [스톡 속성](#stock-properties)을 참조하세요.

  |인터페이스 유형|설명|
  |--------------------|-----------------|
  |ATL 이중 인터페이스, 사용자 지정 인터페이스 및 로컬 사용자 지정 인터페이스|속성 이름을 제공합니다.|
  |MFC dispinterface, MFC ActiveX 컨트롤 dispinterface|속성 이름을 입력하거나 목록에서 스톡 속성을 선택합니다. 목록에서 속성을 선택하면 **속성 형식** 상자에 적절한 값이 표시됩니다. **구현 형식**에서 선택한 항목에 따라 이 형식을 변경할 수 있습니다.|

- **반환 형식**

  ATL 인터페이스 전용. 속성의 반환 형식을 설정합니다. 이중 인터페이스의 경우, `HRESULT`는 항상 반환 형식이며 이 상자는 사용할 수 없습니다. 사용자 지정 인터페이스의 경우, 목록에서 반환 형식을 선택할 수 있습니다. `HRESULT`은 오류를 반환하는 표준 방식을 제공하기 때문에 여전히 권장됩니다.

- **변수 이름**

  MFC dispinterface 전용. **구현 형식**에서 **멤버 변수**를 지정한 경우에만 사용할 수 있습니다. 속성이 연결된 멤버 변수의 이름을 설정합니다. 기본적으로 변수 이름은 `m_`*PropertyName*으로 설정됩니다. 이 이름을 편집할 수 있습니다.

- **알림 함수**

  MFC dispinterface 전용. **구현 형식**에서 **멤버 변수**를 지정한 경우에만 사용할 수 있습니다. 속성이 변경될 경우 호출되는 알림 함수의 이름을 설정합니다. 기본적으로 알림 함수의 이름은 `On`*PropertyName*`Changed`로 설정됩니다. 이 이름을 편집할 수 있습니다.

- **Get 함수**

  MFC dispinterface용. **구현 형식**에서 **Get/Set 메서드**를 지정한 경우에만 사용할 수 있습니다. 속성을 가져올 함수의 이름을 설정합니다. 기본적으로 `Get` 함수의 이름은 `Get`*PropertyName*으로 설정됩니다. 이 이름을 편집할 수 있습니다. 이 이름을 삭제하면 [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) 함수가 인터페이스 디스패치 맵에 삽입됩니다. `Get`*PropertyName* 함수는 속성을 읽을 수 있는 것으로 지정합니다.

- **Set 함수**

  MFC dispinterface 전용. **구현 형식**에서 **Get/Set 메서드**를 지정한 경우에만 사용할 수 있습니다. 속성을 설정할 함수의 이름을 설정합니다. 기본적으로 `Set` 함수의 이름은 `Set`*PropertyName*으로 설정됩니다. 이 이름을 편집할 수 있습니다. 이 이름을 삭제하면 [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) 함수가 인터페이스 디스패치 맵에 삽입됩니다. `Set`*PropertyName* 함수는 속성을 작성할 수 있는 것으로 지정합니다.

- **구현 형식**

  MFC dispinterface 전용. 추가하는 속성을 구현하는 방법을 지정합니다.

  |구현 형식|설명|
  |-------------------------|-----------------|
  |**스톡**|**속성 이름**에서 선택한 속성의 스톡 구현을 지정합니다. 기본값입니다. 자세한 내용은 [스톡 속성](#stock-properties)을 참조하세요.<br /><br /> **스톡**을 지정한 후에는 **속성 형식**, **매개 변수 형식** 및 **매개 변수 이름**이 흐리게 표시됩니다.|
  |**멤버 변수**|속성이 멤버 변수로 추가되도록 지정합니다. 사용자 지정 속성 또는 대부분의 스톡 속성을 멤버 변수로 추가할 수 있습니다. `Caption`, `hWnd` 및 `Text` 속성에 대한 **멤버 변수**를 지정할 수 없습니다.<br /><br /> **변수 이름** 및 **알림 함수**에 기본 이름을 제공합니다. 이 이름을 편집할 수 있습니다.|
  |**Get/Set 메서드**|기본적으로 속성을 `Get`*PropertyName* 및 `Set`*PropertyName* 함수로 추가하도록 지정합니다. 이러한 이름은 **Get 함수** 및 **Set 함수** 아래에 나타납니다.<br /><br /> Get 함수의 값을 전달하는 기본 **속성 형식**을 변경할 수 있습니다. `Get` 및 `Set` 함수에 대한 매개 변수를 지정할 수 있습니다.|

- **Get 함수**

  ATL 인터페이스용. 속성을 읽을 수 있도록 설정합니다. 즉, 개체에서 이 속성을 검색하기 위해 `Get` 메서드를 만듭니다. **Get**, **Put** 또는 모두를 선택합니다.

- **Put 함수**

  ATL 인터페이스 전용. 속성을 쓰기 가능으로 설정합니다. 즉, 개체의 이 속성을 설정하거나 "배치"하기 위해 `Put` 메서드를 만듭니다. **Get**, **Put** 또는 모두를 선택합니다. 이 옵션을 선택하면 다음 두 가지 메서드 구현 방법 중에서 선택할 수 있습니다.

  |옵션|설명|
  |------------|-----------------|
  |**PropPut**|[PropPut](../windows/attributes/propput.md) 함수는 개체의 복사본을 반환합니다. 속성을 쓰기 가능하도록 만드는 기본적이고 가장 일반적인 방법입니다.|
  |**PropPutRef**|[PropPutRef](../windows/attributes/propputref.md) 함수는 개체 자체의 복사본을 반환하지 않고 개체에 대한 참조를 반환합니다. 큰 구조체 또는 배열과 같은 초기화 오버헤드가 있을 수 있는 개체에는 이 옵션을 사용하는 것이 좋습니다.|

- **매개 변수 특성**

  ATL 인터페이스 전용. **매개 변수 이름**에서 지정된 매개 변수가 `in`, `out`, 모두 또는 없음인지를 설정합니다.

  |옵션|설명|
  |------------|-----------------|
  |`in`|호출하는 프로시저에서 호출된 프로시저로 매개 변수가 전달됩니다.|
  |`out`|포인터 매개 변수는 호출된 프로시저에서 호출하는 프로시저로(서버에서 클라이언트로) 반환됩니다.|

- **매개 변수 형식**

  매개 변수의 데이터 형식을 설정합니다. 목록에서 형식을 선택합니다.

- **매개 변수 이름**

  속성에 매개 변수가 있는 경우 속성에 추가하는 매개 변수의 이름을 설정합니다. **추가**를 선택하면 매개 변수 이름이 **매개 변수 목록**에 나타납니다.

- **매개 변수 목록**

  속성에 추가할 특성 목록을 표시합니다. 목록의 각 항목은 매개 변수 이름, 매개 변수 형식 및 특성으로 구성됩니다. **추가** 및 **제거**를 사용하여 목록을 업데이트합니다.

- **추가**

  **매개 변수 이름** 및 **매개 변수 형식**에서 지정한 매개 변수를 **매개 변수 목록**에 추가합니다. **추가**를 선택하여 목록에 매개 변수를 추가합니다.

- **제거**

  **매개 변수 목록**에서 선택한 매개 변수를 제거합니다.

- **기본 속성**

  MFC dispinterface 전용. 이 속성을 인터페이스의 기본값으로 설정합니다. 기본 속성을 지정하면 인터페이스에는 하나의 기본 속성만 있을 수 있으며, 인터페이스에 추가하는 다른 모든 속성에 이 상자를 사용할 수 없습니다.

## <a name="idl-attributes-add-property-wizard"></a>IDL 특성, 속성 추가 마법사

이 속성에 대한 IDL(인터페이스 정의 언어) 설정을 지정하려면 이 속성 추가 마법사 페이지를 사용합니다.

- `id`

  속성을 식별하는 숫자 ID를 설정합니다. 이 옵션은 사용자 지정 인터페이스의 속성에 사용할 수 없습니다. *MIDL 참조*에서 [id](/windows/win32/Midl/id)를 확인합니다.

- `helpcontext`

  도움말 파일에서 이 속성에 대한 정보를 볼 수 있는 컨텍스트 ID를 지정합니다. *MIDL 참조*에서 [helpcontext](/windows/win32/Midl/helpcontext)를 확인합니다.

- `helpstring`

  적용되는 요소를 설명하는 데 사용되는 문자열을 지정합니다. 기본적으로 **`property`** &nbsp;속성&nbsp;이름으로 설정됩니다. *MIDL 참조*에서 [helpstring](/windows/win32/Midl/helpstring)을 확인합니다.

### <a name="other-options"></a>기타 옵션

일부 옵션은 모든 속성 유형에 대해 사용할 수 있습니다.

|옵션|설명|
|------------|-----------------|
|`bindable`|속성이 데이터 바인딩을 지원합니다. *MIDL 참조*에서 [bindable](/windows/win32/Midl/bindable)을 확인합니다. 속성의 스톡 구현의 경우 기본적으로 이 옵션이 설정되며 변경할 수 없습니다.|
|`defaultbind`|개체를 가장 잘 보여주는 바인딩할 수 있는 단일 속성임을 나타탭니다. *MIDL 참조*에서 [defaultbind](/windows/win32/Midl/defaultbind)를 확인합니다.|
|`displaybind`|사용자에게 바인딩할 수 있는 속성으로 표시합니다. *MIDL 참조*에서 [displaybind](/windows/win32/Midl/displaybind)를 확인합니다.|
|`immediatebind`|데이터 바인딩된 개체의 이 속성에 대한 모든 변경 내용을 데이터베이스에 즉시 알립니다. *MIDL 참조*에서 [immediatebind](/windows/win32/Midl/immediatebind)를 확인합니다.|
|`defaultcollelem`|속성은 기본 컬렉션의 요소에 대한 접근자 함수입니다. *MIDL 참조*에서 [defaultcollelem](/windows/win32/Midl/defaultcollelem)을 확인합니다.|
|`nonbrowsable`|속성 브라우저에 표시하지 않아야 할 인터페이스 또는 dispinterface 멤버의 태그를 지정합니다. *MIDL 참조*에서 [nonbrowsable](/windows/win32/Midl/nonbrowsable)을 확인합니다.|
|`requestedit`|속성이 `OnRequestEdit` 알림을 지원함을 나타냅니다. *MIDL 참조*에서 [requestedit](/windows/win32/Midl/requestedit)를 참조하세요. 속성의 스톡 구현의 경우 기본적으로 이 옵션이 설정되며 변경할 수 없습니다.|
|`source`|속성의 멤버가 이벤트의 소스입니다. *MIDL 참조*에서 [source](/windows/win32/Midl/source)를 확인합니다.|
|`hidden`|속성이 존재하지만 사용자 기반 브라우저에는 표시되지 않아야 함을 나타냅니다. *MIDL 참조*에서 [hidden](/windows/win32/Midl/hidden)을 확인합니다.|
|`restricted`|임의로 속성을 호출할 수 없도록 지정합니다. *MIDL 참조*에서 [restricted](/windows/win32/Midl/restricted)를 확인합니다.|
|`local`|속성이 원격이 아니라고 MIDL 컴파일러에 지정합니다. *MIDL 참조*에서 [local](/windows/win32/Midl/local)을 확인합니다.|

## <a name="stock-properties"></a>스톡 속성

[속성 추가 마법사](#idl-attributes-add-property-wizard)를 사용하여 MFC dispinterface에 속성을 추가하는 경우 마법사의 [이름](#names-add-property-wizard) 페이지에 있는 **속성 이름** 목록에서 스톡 속성을 선택할 수 있습니다. 속성은 다음과 같습니다.

|속성 이름|설명|
|-------------------|-----------------|
|`Appearance`|컨트롤의 모양을 결정하는 값을 반환하거나 설정합니다. 컨트롤의 `Appearance` 속성은 3차원 표시 효과를 포함하거나 생략할 수 있습니다. 이 속성은 앰비언트 읽기/쓰기 속성입니다.|
|`BackColor`|색상표(RGB) 색 또는 미리 정의된 시스템 색에 대한 컨트롤의 앰비언트 `BackColor` 속성을 반환하거나 설정합니다. 기본적으로 해당 값은 컨트롤 컨테이너의 전경색에 해당합니다. 이 속성은 앰비언트 읽기/쓰기 속성입니다.|
|`BorderStyle`|컨트롤의 테두리 스타일을 반환하거나 설정합니다. 이 속성은 읽기/쓰기 속성입니다.|
|`Caption`|컨트롤의 `Caption` 속성을 반환하거나 설정합니다. 캡션은 창의 제목입니다. `Caption`에는 **멤버 변수** 구현 형식이 없습니다.|
|`Enabled`|컨트롤의 `Enabled` 속성을 반환하거나 설정합니다. 사용 가능한 컨트롤은 사용자가 만든 이벤트에 대응할 수 있습니다.|
|`Font`|컨트롤의 앰비언트 글꼴을 반환하거나 설정합니다. 컨트롤에 글꼴이 없으면 Null입니다.|
|`ForeColor`|컨트롤의 앰비언트 `ForeColor` 속성을 반환하거나 설정합니다.|
|`hWnd`|컨트롤의 `hWnd` 속성을 반환하거나 설정합니다. `hWnd`에는 **멤버 변수** 구현 형식이 없습니다.|
|`ReadyState`|컨트롤의 `ReadyState` 속성을 반환하거나 설정합니다. 컨트롤이는 초기화되지 않거나, 초기화되거나, 로드되거나, 대화형이거나, 완료될 수 있습니다. 자세한 정보는 *인터넷 SDK*에서 [READYSTATE](/previous-versions/aa768362\(v=vs.85\))를 참조하세요.|
|`Text`|컨트롤에 포함된 텍스트를 반환하거나 설정합니다. `Text`에는 **멤버 변수** 구현 형식이 없습니다.|
