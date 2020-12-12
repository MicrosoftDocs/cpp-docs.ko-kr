---
description: 'MFC ActiveX 컨트롤: ActiveX 컨트롤에서 데이터 바인딩 사용에 대 한 자세한 정보'
title: 'MFC ActiveX 컨트롤: ActiveX 컨트롤에서 데이터 바인딩 사용'
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: eb6a6ea52dee7aaf1fcb4c9f15db89cfa5f25deb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206086"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 컨트롤: ActiveX 컨트롤에서 데이터 바인딩 사용

ActiveX 컨트롤의 보다 강력한 사용 중 하나는 데이터 바인딩입니다 .이를 통해 컨트롤의 속성을 데이터베이스의 특정 필드에 바인딩할 수 있습니다. 사용자가이 바인딩된 속성의 데이터를 수정 하면 컨트롤에서 데이터베이스에 알리고 레코드 필드가 업데이트 되도록 요청 합니다. 그런 다음 데이터베이스는 요청의 성공 또는 실패를 제어 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

이 문서에서는 작업의 제어 측면을 설명 합니다. 데이터베이스와의 데이터 바인딩 상호 작용을 구현 하는 것은 제어 컨테이너의 책임입니다. 컨테이너에서 데이터베이스 상호 작용을 관리 하는 방법은이 설명서의 범위를 벗어나는 것입니다. 데이터 바인딩에 대 한 컨트롤을 준비 하는 방법은이 문서의 나머지 부분에 설명 되어 있습니다.

![데이터&#45;바인딩된 컨트롤의 개념적 다이어그램](../mfc/media/vc374v1.gif "데이터&#45;바인딩된 컨트롤의 개념적 다이어그램") <br/>
Data-Bound 컨트롤의 개념적 다이어그램

`COleControl`클래스는 데이터 바인딩을 구현 하기 쉬운 프로세스를 만드는 두 개의 멤버 함수를 제공 합니다. 첫 번째 함수인 [BoundPropertyRequestEdit](reference/colecontrol-class.md#boundpropertyrequestedit)는 속성 값을 변경할 수 있는 권한을 요청 하는 데 사용 됩니다. 두 번째 함수인 [BoundPropertyChanged](reference/colecontrol-class.md#boundpropertychanged)는 속성 값이 성공적으로 변경 된 후에 호출 됩니다.

이 문서는 다음 항목을 설명합니다.

- [바인딩 가능한 스톡 속성 만들기](#vchowcreatingbindablestockproperty)

- [바인딩 가능한 Get/Set 메서드 만들기](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a> 바인딩 가능한 스톡 속성 만들기

[바인딩 가능한 get/set 메서드](#vchowcreatingbindablegetsetmethod)를 원하는 경우에도 데이터 바인딩된 스톡 속성을 만들 수 있습니다.

> [!NOTE]
> 스톡 속성에는 `bindable` `requestedit` 기본적으로 및 특성이 있습니다.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 바인딩 가능한 스톡 속성을 추가 하려면

1. [MFC ActiveX 컨트롤 마법사](reference/mfc-activex-control-wizard.md)를 사용 하 여 프로젝트를 시작 합니다.

1. 컨트롤의 인터페이스 노드를 마우스 오른쪽 단추로 클릭 합니다.

   바로 가기 메뉴가 열립니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가** 를 클릭 합니다.

1. **속성 이름** 드롭다운 목록에서 항목 중 하나를 선택 합니다. 예를 들어 **텍스트** 를 선택할 수 있습니다.

   **텍스트** 는 스톡 속성 이므로 **바인딩** 가능 및 **requestedit** 특성은 이미 확인 되었습니다.

1. **IDL 특성** 탭: **displaybind** 및 **defaultbind** 에서 다음 확인란을 선택 하 여 프로젝트의 속성 정의에 특성을 추가 합니다. IDL 파일. 이러한 특성은 컨트롤을 사용자에 게 표시 하 고 스톡 속성을 바인딩 가능한 기본 속성으로 설정 합니다.

이 시점에서 컨트롤은 데이터 원본의 데이터를 표시할 수 있지만 사용자가 데이터 필드를 업데이트할 수는 없습니다. 컨트롤에서 데이터를 업데이트할 수 있도록 하려면 다음과 `OnOcmCommand` 같이 [onocmcommand](mfc-activex-controls-subclassing-a-windows-control.md) 함수를 변경 합니다.

[!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

이제 컨트롤을 등록 하는 프로젝트를 빌드할 수 있습니다. 대화 상자에 컨트롤을 삽입 하면 **데이터 필드** 및 **데이터 원본** 속성이 추가 되 고 컨트롤에 표시할 데이터 원본 및 필드를 선택할 수 있습니다.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a> 바인딩 가능한 Get/Set 메서드 만들기

데이터 바인딩된 get/set 메서드 외에도 [바인딩 가능한 스톡 속성](#vchowcreatingbindablestockproperty)을 만들 수 있습니다.

> [!NOTE]
> 이 절차에서는 Windows 컨트롤을 서브클래싱하는 ActiveX 컨트롤 프로젝트가 있다고 가정 합니다.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 바인딩 가능한 get/set 메서드를 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. **컨트롤 설정** 페이지에서 서브 클래스에 대 한 컨트롤의 창 클래스를 선택 합니다. 예를 들어 편집 컨트롤의 서브 클래스를 사용할 수 있습니다.

1. 컨트롤의 프로젝트를 로드합니다.

1. 컨트롤의 인터페이스 노드를 마우스 오른쪽 단추로 클릭 합니다.

   바로 가기 메뉴가 열립니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가** 를 클릭 합니다.

1. 속성 **이름** 상자에 속성 이름을 입력 합니다. `MyProp`이 예에서는를 사용 합니다.

1. **속성 유형** 드롭다운 목록 상자에서 데이터 형식을 선택 합니다. **`short`** 이 예에서는를 사용 합니다.

1. **구현 형식** 에서 **Get/Set 메서드** 를 클릭합니다.

1. IDL 특성 탭에서 **바인딩** 가능, **requestedit**, **displaybind** 및 **defaultbind** 확인란을 선택 하 여 프로젝트의 속성 정의에 특성을 추가 합니다. IDL 파일. 이러한 특성은 컨트롤을 사용자에 게 표시 하 고 스톡 속성을 바인딩 가능한 기본 속성으로 설정 합니다.

1. **Finish** 를 클릭합니다.

1. 다음 코드가 포함 되도록 함수 본문을 수정 합니다 `SetMyProp` .

   [!code-cpp[NVC_MFC_AxData#2](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. 및 함수에 전달 되는 매개 변수는의 `BoundPropertyChanged` `BoundPropertyRequestEdit` 속성에 대 한 id () 특성에 전달 된 매개 변수인 속성의 dispid입니다. IDL 파일.

1. 다음 코드를 포함 하도록 [Onocmcommand](mfc-activex-controls-subclassing-a-windows-control.md) 함수를 수정 합니다.

   [!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. `OnDraw`다음 코드를 포함 하도록 함수를 수정 합니다.

   [!code-cpp[NVC_MFC_AxData#3](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. 헤더 파일의 public 섹션에 컨트롤 클래스의 헤더 파일을 추가 하려면 멤버 변수에 대 한 다음 정의 (생성자)를 추가 합니다.

   [!code-cpp[NVC_MFC_AxData#4](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. 함수의 마지막 줄을 다음 줄로 설정 합니다 `DoPropExchange` .

   [!code-cpp[NVC_MFC_AxData#5](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. `OnResetState`다음 코드를 포함 하도록 함수를 수정 합니다.

   [!code-cpp[NVC_MFC_AxData#6](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. `GetMyProp`다음 코드를 포함 하도록 함수를 수정 합니다.

   [!code-cpp[NVC_MFC_AxData#7](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

이제 컨트롤을 등록 하는 프로젝트를 빌드할 수 있습니다. 대화 상자에 컨트롤을 삽입 하면 **데이터 필드** 및 **데이터 원본** 속성이 추가 되 고 컨트롤에 표시할 데이터 원본 및 필드를 선택할 수 있습니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
