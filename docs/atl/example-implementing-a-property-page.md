---
title: 속성 페이지(ATL) 구현
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 82c2bd3765802f87025eaf2dfbda8f7467bbe9a0
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921245"
---
# <a name="example-implementing-a-property-page"></a>예제: 속성 페이지 구현

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL 속성 페이지 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

이 예제에서는 [문서 클래스](../mfc/document-classes.md) 인터페이스의 속성을 표시하고 변경을 허용하는 속성 페이지를 빌드하는 방법을 보여 줍니다.

예제는 [ATLPages 샘플](../overview/visual-cpp-samples.md)을 기반으로 합니다.

이 예제를 완료하려면 다음을 수행합니다.

- 클래스 추가 대화 상자 및 ATL 속성 페이지 마법사를 사용하여 [ATL 속성 페이지 클래스를 추가](#vcconusing_the_atl_object_wizard)합니다.

- `Document` 인터페이스의 흥미로운 속성에 대한 새 컨트롤을 추가하여 [대화 상자 리소스를 편집](#vcconediting_the_dialog_resource)합니다.

- 사용자가 변경한 내용을 속성 페이지 사이트에 알리는 [메시지 처리기를 추가](#vcconadding_message_handlers)합니다.

- [하우스키핑](#vcconhousekeeping) 섹션에 몇 개의 `#import` 문과 typedef를 추가합니다.

- 속성 페이지에 전달되는 개체의 유효성을 검사하도록 [IPropertyPageImpl::SetObjects를 재정의](#vcconoverriding_ipropertypageimpl_setobjects)합니다.

- 속성 페이지의 인터페이스를 초기화하도록 [IPropertyPageImpl::Activate를 재정의](#vcconoverriding_ipropertypageimpl_activate)합니다.

- 개체를 최신 속성 값으로 업데이트하도록 [IPropertyPageImpl::Apply를 재정의](#vcconoverride_ipropertypageimpl_apply)합니다.

- 간단한 도우미 개체를 만들어 [속성 페이지를 표시](#vccontesting_the_property_page)합니다.

- 속성 페이지를 테스트할 [매크로를 만듭니다](#vcconcreating_a_macro).

## <a name="adding-the-atl-property-page-class"></a><a name="vcconusing_the_atl_object_wizard"></a> ATL 속성 페이지 클래스 추가

먼저 DLL 서버에 대해 `ATLPages7`이라는 새 ATL 프로젝트를 만듭니다. 이제 [ATL 속성 페이지 마법사](../atl/reference/atl-property-page-wizard.md)를 사용하여 속성 페이지를 생성합니다. 속성 페이지의 **짧은 이름** 으로 **DocProperties** 를 지정한 다음, **문자열** 페이지로 전환하여 아래 표에 나와 있는 속성 페이지 관련 항목을 설정합니다.

|항목|값|
|----------|-----------|
|제목|TextDocument|
|문서 문자열|VCUE TextDocument 속성|
|Helpfile|*\<blank>*|

이 마법사 페이지에서 설정한 값은 `IPropertyPage::GetPageInfo`를 호출할 때 속성 페이지 컨테이너로 반환됩니다. 그 이후의 문자열 처리는 컨테이너에 따라 다르지만, 일반적으로 사용자에게 페이지를 식별하는 데 사용됩니다. 제목은 일반적으로 페이지 위쪽의 탭에 표시되고, 문서 문자열은 상태 표시줄이나 도구 설명에 표시될 수 있습니다(표준 속성 프레임에서는 이 문자열이 사용되지 않음).

> [!NOTE]
> 여기서 설정한 문자열은 마법사에 의해 문자열 리소스로 프로젝트에 저장됩니다. 페이지의 코드를 생성한 후에 이 정보를 변경해야 하는 경우 리소스 편집기를 사용하여 이러한 문자열을 쉽게 편집할 수 있습니다.

**확인** 을 클릭하면 마법사에서 속성 페이지를 생성합니다.

## <a name="editing-the-dialog-resource"></a><a name="vcconediting_the_dialog_resource"></a> 대화 상자 리소스 편집

속성 페이지가 생성되었으므로, 이제 페이지를 나타내는 대화 상자 리소스에 몇 개의 컨트롤을 추가해야 합니다. 편집 상자, 정적 텍스트 컨트롤, 확인란을 하나씩 추가하고 아래와 같이 ID를 설정합니다.

![대화 상자 리소스 편집](../atl/media/ppgresourcelabeled.gif "대화 상자 리소스 편집")

이러한 컨트롤은 문서의 파일 이름과 읽기 전용 상태를 표시하는 데 사용됩니다.

> [!NOTE]
> 대화 상자 리소스는 프레임 또는 명령 단추를 포함하지 않으며, 예상과 달리 탭 모양도 아닙니다. 이러한 기능은 [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe)을 호출하여 만든 것과 같은 속성 페이지 프레임에서 제공합니다.

## <a name="adding-message-handlers"></a><a name="vcconadding_message_handlers"></a> 메시지 처리기 추가

컨트롤이 배치되고 나면, 컨트롤의 값이 변경될 때 페이지의 변경 상태를 업데이트하는 메시지 처리기를 추가할 수 있습니다.

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

이 코드는 편집 컨트롤 또는 확인란의 변경 내용에 응답하여 [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)를 호출하고, 여기서 페이지가 변경되었음을 페이지 사이트에 알립니다. 일반적으로, 이 알림에 대한 응답으로 페이지 사이트의 속성 페이지 프레임에서 **적용** 단추가 활성화되거나 비활성화됩니다.

> [!NOTE]
> 변경되지 않은 속성의 업데이트를 방지할 수 있도록, 사용자가 변경한 속성을 고유한 속성 페이지에서 정확하게 추적해야 할 수도 있습니다. 이 예제에서는 원래 속성 값을 추적하고, 변경 내용을 적용할 때 UI의 현재 값과 비교하여 해당 코드를 구현합니다.

## <a name="housekeeping"></a><a name="vcconhousekeeping"></a> 하우스키핑

이제 컴파일러에서 `Document` 인터페이스에 대해 알 수 있도록 몇 개의 `#import` 문을 DocProperties.h에 추가합니다.

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

또한 기본 클래스를 참조 하 `IPropertyPageImpl` 고 클래스에 다음을 추가 해야 합니다 **`typedef`** `CDocProperties` .

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

## <a name="overriding-ipropertypageimplsetobjects"></a><a name="vcconoverriding_ipropertypageimpl_setobjects"></a> IPropertyPageImpl::SetObjects 재정의

재정의해야 하는 첫 번째 `IPropertyPageImpl` 메서드는 [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)입니다. 여기서는 단일 개체만 전달되었는지, 예상되는 `Document` 인터페이스를 지원하는지 확인하는 코드를 추가하겠습니다.

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
> 사용자가 개체의 파일 이름을 설정할 수 있도록 허용할 예정이므로, 어떤 위치에 있든 파일 한 개만 존재할 수 있도록 이 페이지에 대해 단일 개체만 지원하는 것이 타당합니다.

## <a name="overriding-ipropertypageimplactivate"></a><a name="vcconoverriding_ipropertypageimpl_activate"></a> IPropertyPageImpl::Activate 재정의

다음 단계로, 페이지를 처음 만들 때 기본 개체의 속성 값을 사용하여 속성 페이지를 초기화합니다.

이 경우에는 페이지 사용자가 변경 내용을 적용할 때 초기 속성 값도 비교에 사용하므로 클래스에 다음 멤버를 추가해야 합니다.

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

[Activate](../atl/reference/ipropertypageimpl-class.md#activate) 메서드의 기본 클래스 구현에서 대화 상자와 해당 컨트롤을 만들기 때문에, 이 메서드를 재정의하고 기본 클래스 호출 뒤에 고유 초기화를 추가할 수 있습니다.

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

이 코드에서는 `Document` 인터페이스의 COM 메서드를 사용하여 관심 있는 속성을 가져옵니다. 그런 다음, [CDialogImpl](../atl/reference/cdialogimpl-class.md)에서 제공하는 Win32 API 래퍼와 해당 기본 클래스를 사용하여 사용자에게 속성 값을 표시합니다.

## <a name="overriding-ipropertypageimplapply"></a><a name="vcconoverride_ipropertypageimpl_apply"></a> IPropertyPageImpl::Apply 재정의

사용자가 변경 내용을 개체에 적용하려고 하면, 속성 페이지 사이트에서 [Apply](../atl/reference/ipropertypageimpl-class.md#apply) 메서드를 호출합니다. 여기서는 `Activate`의 코드와 반대 작업을 수행합니다. `Activate`는 개체에서 값을 가져와 속성 페이지의 컨트롤에 푸시한 반면, `Apply`는 속성 페이지의 컨트롤에서 값을 가져와 개체에 푸시합니다.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
> 이 구현의 시작 부분에 있는 [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) 검사는 `Apply`가 두 번 이상 호출될 경우 개체의 불필요한 업데이트를 방지하기 위한 초기 검사입니다. 이 밖에도 변경 내용이 있을 때만 `Document`에 대한 메서드 호출이 발생하도록 하는 각 속성 값 검사가 있습니다.

> [!NOTE]
> `Document`는 `FullName`을 읽기 전용 속성으로 공개합니다. 속성 페이지의 변경 내용에 따라 문서의 파일 이름을 업데이트하려면 `Save` 메서드를 사용하여 파일을 다른 이름으로 저장해야 합니다. 따라서 속성 페이지의 코드를 속성 가져오기 또는 설정으로 제한하지 않아도 됩니다.

## <a name="displaying-the-property-page"></a><a name="vccontesting_the_property_page"></a> 속성 페이지 표시

이 페이지를 표시하려면 간단한 도우미 개체를 만들어야 합니다. 도우미 개체는 단일 개체에 연결된 단일 페이지를 표시하기 위한 `OleCreatePropertyFrame` API를 간소화하는 메서드를 제공합니다. 이 도우미는 Visual Basic에서 사용할 수 있도록 설계됩니다.

[클래스 추가 대화 상자](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 및 [ATL 단순 개체 마법사](../atl/reference/atl-simple-object-wizard.md)를 사용하여 새 클래스를 생성하고 짧은 이름으로 `Helper`를 사용합니다. 클래스가 생성되면, 아래 표와 같이 메서드를 추가합니다.

|항목|값|
|----------|-----------|
|메서드 이름|`ShowPage`|
|매개 변수|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

*bstrCaption* 매개 변수는 대화 상자의 제목으로 표시할 캡션입니다. *bstrID* 매개 변수는 표시할 속성 페이지의 CLSID 또는 ProgID를 나타내는 문자열입니다. *pUnk* 매개 변수는 속성 페이지에서 속성을 구성할 개체의 `IUnknown` 포인터입니다.

아래와 같이 메서드를 구현합니다.

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

## <a name="creating-a-macro"></a><a name="vcconcreating_a_macro"></a> 매크로 만들기

프로젝트를 빌드했으면, Visual Studio 개발 환경에서 만들고 실행할 수 있는 간단한 매크로를 사용하여 속성 페이지와 도우미 개체를 테스트할 수 있습니다. 이 매크로는 도우미 개체를 만든 다음, **DocProperties** 속성 페이지의 ProgID 및 Visual Studio 편집기에서 현재 활성화된 문서의 `IUnknown` 포인터를 사용하여 해당 `ShowPage` 메서드를 호출합니다. 이 매크로에 필요한 코드는 다음과 같습니다.

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

이 매크로를 실행하면 현재 활성화된 텍스트 문서의 파일 이름 및 읽기 전용 상태를 보여 주는 속성 페이지가 표시됩니다. 문서의 읽기 전용 상태는 개발 환경에서 문서에 쓸 수 있는지 여부만 반영하고, 디스크에 있는 파일의 읽기 전용 특성에는 영향을 주지 않습니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[속성 페이지](../atl/atl-com-property-pages.md)<br/>
[ATLPages 샘플](../overview/visual-cpp-samples.md)
