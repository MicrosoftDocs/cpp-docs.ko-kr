---
description: '자세한 정보: ATL 컨트롤 포함 FAQ'
title: ATL 컨트롤 포함 FAQ
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 5c5d3d452a119908cb6c8dcdb08da3276db78f51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165773"
---
# <a name="atl-control-containment-faq"></a>ATL 컨트롤 포함 FAQ

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>어떤 ATL 클래스가 ActiveX 컨트롤 포함에 도움이 되나요?

ATL의 컨트롤 호스팅 코드에서는 ATL 클래스를 사용할 필요가 없습니다. 단순히 **"AtlAxWin80"** 창을 만들고 필요한 경우 컨트롤 호스팅 API를 사용할 수 있습니다. 자세한 내용은 **ATL Control-Hosting api** 를 참조 하세요. 그러나 다음 클래스를 사용 하면 포함 기능을 보다 쉽게 사용할 수 있습니다.

|클래스|설명|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|창을 만들고, 컨트롤을 만들거나, 창에 컨트롤을 연결 하 고, 호스트 개체에 대 한 인터페이스 포인터를 검색 하는 메서드를 제공 하는 **"AtlAxWin80"** 창을 래핑합니다.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|창을 만들고, 컨트롤을 만들거나, 사용이 허가 된 컨트롤을 창에 연결 하 고, 호스트 개체에 대 한 인터페이스 포인터를 검색 하는 메서드를 제공 하는 **"AtlAxWinLic80"** 창을 래핑합니다.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|대화 상자 리소스를 기반으로 하는 ActiveX 컨트롤 클래스의 기본 클래스 역할을 합니다. 이러한 컨트롤에는 다른 ActiveX 컨트롤이 포함 될 수 있습니다.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|대화 상자 리소스를 기반으로 하는 대화 상자 클래스의 기본 클래스 역할을 합니다. 이러한 대화 상자에는 ActiveX 컨트롤이 포함 될 수 있습니다.|
|[CWindow](../atl/reference/cwindow-class.md)|호스트 창의 ID가 지정 된 경우 컨트롤에 대 한 인터페이스 포인터를 반환 하는 [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)메서드를 제공 합니다. 또한에서 노출 하는 Windows API 래퍼는 `CWindow` 일반적으로 창 관리를 용이 하 게 합니다.|

## <a name="what-is-the-atl-control-hosting-api"></a>ATL 컨트롤 호스팅 API란 무엇인가요?

ATL의 컨트롤 호스팅 API는 모든 창이 ActiveX 컨트롤 컨테이너 역할을 하도록 허용 하는 함수 집합입니다. 이러한 함수는 소스 코드로 사용할 수 있고 ATL90.dll에 의해 노출 되기 때문에 프로젝트에 정적 또는 동적으로 연결할 수 있습니다. 컨트롤 호스팅 함수는 아래 표에 나열 되어 있습니다.

|함수|설명|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|호스트 개체를 만들어 제공 된 창에 연결 하 고 기존 컨트롤을 연결 합니다.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|호스트 개체를 만들어 제공 된 창에 연결한 다음 컨트롤을 로드 합니다.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|사용이 허가 된 ActiveX 컨트롤을 만들고, 초기화 하 고, [Atlaxcreatecontrol](reference/composite-control-global-functions.md#atlaxcreatecontrol)과 비슷하게 지정 된 창에서 호스팅합니다.|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|호스트 개체를 만들어 제공 된 창에 연결한 다음 컨트롤을 로드 합니다. 또한 이벤트 싱크를 설정할 수 있습니다.|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|사용이 허가 된 ActiveX 컨트롤을 만들고, 초기화 하 고, [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)와 유사한 지정 된 창에 호스트 합니다.|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|대화 상자 리소스에서 모덜리스 대화 상자를 만들고 창 핸들을 반환 합니다.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|대화 상자 리소스에서 모달 대화 상자를 만듭니다.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|창에서 호스트 되는 컨트롤의 **IUnknown** 인터페이스 포인터를 반환 합니다.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|창에 연결 된 호스트 개체의 **IUnknown** 인터페이스 포인터를 반환 합니다.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|컨트롤 호스팅 코드를 초기화 합니다.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|컨트롤 호스팅 코드를 초기화 하지 않습니다 합니다.|

`HWND`처음 세 함수의 매개 변수는 (거의) 모든 형식의 기존 창 이어야 합니다. 이러한 세 함수 중 하나를 명시적으로 호출 하는 경우 (일반적으로는 필요 하지 않음) 이미 호스트 역할을 하는 창에 핸들을 전달 하지 마십시오. 이렇게 하면 기존 호스트 개체가 해제 되지 않습니다.

처음 7 개의 함수는 [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) 를 암시적으로 호출 합니다.

> [!NOTE]
> 컨트롤 호스팅 API는 ActiveX 컨트롤 포함에 대 한 ATL 지원의 기반을 형성 합니다. 그러나를 활용 하거나 ATL의 래퍼 클래스를 완전히 사용 하는 경우 일반적으로 이러한 함수를 직접 호출할 필요가 거의 없습니다. 자세한 내용은 [ActiveX 컨트롤 포함을 활용 하는 ATL 클래스](#which-atl-classes-facilitate-activex-control-containment)를 참조 하세요.

## <a name="what-is-atlaxwin100"></a>AtlAxWin100이란 무엇인가요?

`AtlAxWin100` 는 ATL의 컨트롤 호스팅 기능을 제공 하는 데 도움이 되는 창 클래스의 이름입니다. 이 클래스의 인스턴스를 만들면 창 프로시저에서 자동으로 컨트롤 호스팅 API를 사용 하 여 창과 연결 된 호스트 개체를 만들고 사용자가 창의 제목으로 지정 하는 컨트롤을 사용 하 여 로드 합니다.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>언제 AtlAxWinInit를 호출해야 하나요?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) 는 **"AtlAxWin80"** 창 클래스와 몇 가지 사용자 지정 창 메시지를 등록 하므로 호스트 창을 만들기 전에이 함수를 호출 해야 합니다. 그러나 호스팅 Api와이 함수를 사용 하는 클래스가 종종이 함수를 호출 하기 때문에이 함수는 항상 명시적으로 호출할 필요가 없습니다. 이 함수를 두 번 이상 호출 하는 것에는 나쁜 영향을 주지 않습니다.

## <a name="what-is-a-host-object"></a>호스트 개체란 무엇인가요?

호스트 개체는 특정 창에 대해 ATL에서 제공 하는 ActiveX 컨트롤 컨테이너를 나타내는 COM 개체입니다. 호스트 개체는 컨트롤에 메시지를 반영할 수 있도록 컨테이너 창을 서브클래싱하 고, 컨트롤에서 사용 하는 데 필요한 컨테이너 인터페이스를 제공 하 고, 컨트롤의 환경을 구성할 수 있도록 [Iaxwinhostwindow](../atl/reference/iaxwinhostwindow-interface.md) 및 [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) 인터페이스를 노출 합니다.

호스트 개체를 사용 하 여 컨테이너의 앰비언트 속성을 설정할 수 있습니다.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>하나의 창에서 여러 개의 컨트롤을 호스트할 수 있나요?

단일 ATL 호스트 창에서 둘 이상의 컨트롤을 호스트할 수 없습니다. 각 호스트 창은 한 번에 정확히 한 개의 컨트롤을 보유 하도록 디자인 되었습니다 .이를 통해 메시지 리플렉션 및 컨트롤 별 앰비언트 속성을 처리 하는 간단한 메커니즘을 사용할 수 있습니다. 그러나 사용자에 게 단일 창에서 여러 컨트롤을 표시 해야 하는 경우에는 해당 창의 자식으로 여러 호스트 창을 만드는 것이 간단 합니다.

## <a name="can-i-reuse-a-host-window"></a>호스트 창을 다시 사용할 수 있나요?

호스트 창을 다시 사용 하지 않는 것이 좋습니다. 코드의 견고성을 보장 하려면 호스트 창의 수명을 단일 컨트롤의 수명에 연결 해야 합니다.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>언제 AtlAxWinTerm을 호출해야 하나요?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) **"AtlAxWin80"** 창 클래스의 등록을 취소 합니다. 기존 호스트 창이 모두 삭제 된 후에는이 함수를 호출 해야 합니다 (호스트 창을 더 이상 만들 필요가 없는 경우). 이 함수를 호출 하지 않으면 프로세스가 종료 될 때 window 클래스가 자동으로 등록 취소 됩니다.

## <a name="hosting-activex-controls-using-atl-axhost"></a>ATL AXHost를 사용하여 ActiveX 컨트롤 호스팅

이 단원의 샘플에서는 AXHost를 만드는 방법 및 다양 한 ATL 함수를 사용 하 여 ActiveX 컨트롤을 호스트 하는 방법을 보여 줍니다. 또한 호스트 되는 컨트롤에서 컨트롤 및 싱크 이벤트 ( [IDispEventImpl](../atl/reference/idispeventimpl-class.md)사용)에 액세스 하는 방법을 보여 줍니다. 이 샘플에서는 주 창이 나 자식 창에서 Calendar 컨트롤을 호스팅합니다.

기호의 정의를 확인 `USE_METHOD` 합니다. 이 기호의 값을 1에서 8 사이로 변경할 수 있습니다. 기호 값은 컨트롤을 만드는 방법을 결정 합니다.

- 짝수 번호의 값을 지정 `USE_METHOD` 하는 경우 호스트를 만드는 호출에서 창을 서브클래싱하 고 컨트롤 호스트로 변환 합니다. 홀수 번호 값의 경우 코드는 호스트 역할을 하는 자식 창을 만듭니다.

- 값이 1에서 4 사이인 경우 컨트롤에 대 한 `USE_METHOD` 액세스와 이벤트 싱크도 호스트를 만드는 호출에서 수행 됩니다. 5에서 8 사이의 값은 인터페이스에 대 한 호스트를 쿼리하고 싱크를 후크합니다.

다음은 요약입니다.

|USE_METHOD|호스트|액세스 및 이벤트 싱크 제어|함수를 보여 줍니다.|
|-----------------|----------|--------------------------------------|---------------------------|
|1|자식 창|한 단계|CreateControlLicEx|
|2|기본 창|한 단계|AtlAxCreateControlLicEx|
|3|자식 창|한 단계|CreateControlEx|
|4|기본 창|한 단계|AtlAxCreateControlEx|
|5|자식 창|여러 단계|CreateControlLic|
|6|기본 창|여러 단계|AtlAxCreateControlLic|
|7|자식 창|여러 단계|CreateControl|
|8|기본 창|여러 단계|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>참고 항목

[컨트롤 포함 FAQ](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T 클래스](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowLic 인터페이스](../atl/reference/iaxwinhostwindowlic-interface.md)
