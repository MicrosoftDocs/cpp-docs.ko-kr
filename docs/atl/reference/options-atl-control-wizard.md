---
description: '자세히 알아보기: 옵션, ATL 컨트롤 마법사'
title: 옵션, ATL 컨트롤 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 428f6ba1a4bee9cec60ca05b57d66d176c3f0deb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157895"
---
# <a name="options-atl-control-wizard"></a>옵션, ATL 컨트롤 마법사

마법사의이 페이지를 사용 하 여 만들려는 컨트롤의 형식 및 해당 컨트롤에 포함 된 인터페이스 지원 수준을 정의할 수 있습니다.

## <a name="uielement-list"></a>UI 요소 목록

### <a name="control-type"></a>컨트롤 형식

만들려는 컨트롤의 종류입니다.

- **표준 컨트롤**: ActiveX 컨트롤입니다.

- **복합 컨트롤**: 다른 activex 컨트롤 또는 Windows 컨트롤 (대화 상자와 유사)을 포함할 수 있는 activex 컨트롤입니다. 복합 컨트롤에는 다음이 포함 됩니다.

  - 복합 컨트롤을 구현 하는 대화 상자에 대 한 템플릿입니다.

  - 호출 시 복합 컨트롤을 자동으로 등록 하는 사용자 지정 리소스인 REGISTRY

  - 복합 컨트롤을 구현 하는 c + + 클래스입니다.

  - 복합 컨트롤에 의해 노출 되는 COM 인터페이스입니다.

  - 복합 컨트롤을 포함 하는 HTML 테스트 페이지입니다.

    기본적으로이 컨트롤은 [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) 을 true로 설정 하 여이 컨트롤이 창 컨트롤 임을 표시 합니다. 싱크 맵을 구현 합니다. 자세한 내용은 [DHTML 컨트롤에 대 한 지원](../../atl/atl-support-for-dhtml-controls.md)을 참조 하세요.

- **DHTML 컨트롤**: ATL DHTML 컨트롤은 HTML을 사용 하 여 사용자 인터페이스를 지정 합니다. DHTML UI 클래스에는 COM 맵이 포함 되어 있습니다. 기본적으로이 컨트롤은 [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) 을 true로 설정 하 여이 컨트롤이 창 컨트롤 임을 표시 합니다.

   자세한 내용은 [DHTML 컨트롤 프로젝트의 요소 식별](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)을 참조 하세요.

### <a name="minimal-control"></a>최소 컨트롤

는 대부분의 컨테이너에서 절대적으로 필요한 인터페이스만 지원 합니다. 컨트롤 형식에 대 한 **최소 제어** 를 설정할 수 있습니다. 최소 표준 컨트롤, 최소 복합 컨트롤 또는 최소 DHTML 컨트롤을 만들 수 있습니다.

### <a name="aggregation"></a>집계

만드는 컨트롤에 대 한 집계 지원을 추가 합니다. 자세한 내용은 [집계](../../atl/aggregation.md)를 참조 하세요.

- **예**: 집계할 수 있는 컨트롤을 만듭니다.

- **아니요**: 집계할 수 없는 컨트롤을 만듭니다.

- **만** 해당: 집계를 통해서만 인스턴스화할 수 있는 컨트롤을 만듭니다.

### <a name="threading-model"></a>스레딩 모델

컨트롤에서 사용 하는 스레딩 모델을 지정 합니다.

- **단일**: 컨트롤이 기본 COM 스레드에서만 실행 됩니다.

- **아파트**: 모든 단일 스레드 아파트에서 컨트롤을 만들 수 있습니다. 기본값입니다.

### <a name="interface"></a>인터페이스

이 컨트롤이 컨테이너에 노출 하는 인터페이스의 형식입니다.

- **이중**: VTBL을 통해 및 직접 속성 및 메서드를 노출 하는 인터페이스를 만듭니다 `IDispatch` .

- **사용자 지정**: VTBL을 통해 메서드를 직접 노출 하는 인터페이스를 만듭니다.

   **사용자 지정** 을 선택 하는 경우 컨트롤을 **자동화 호환** 으로 지정할 수 있습니다. **자동화 호환** 을 선택 하는 경우 마법사는 IDL의 인터페이스에 [oleautomation](../../windows/attributes/oleautomation.md) 특성을 추가 하 고 인터페이스는 oleaut32.dll의 유니버설 마샬러에 의해 마샬링될 수 있습니다. 자세한 내용은 Windows SDK의 [마샬링 세부 정보](/windows/win32/com/marshaling-details) 를 참조 하세요.

   또한 **자동화 호환** 을 선택 하는 경우 컨트롤의 모든 메서드에 대 한 모든 매개 변수는 변형 호환이 가능 해야 합니다.

### <a name="support"></a>지원

컨트롤에 대 한 기타 추가 지원을 설정 합니다.

- **연결 요소**: 개체의 클래스가 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 에서 파생 되 게 하 고 소스 인터페이스를 노출 하도록 허용 하 여 개체에 대 한 연결 지점이 가능 하도록 합니다.

- **사용이 허가** 됨: [라이선스](/windows/win32/com/licensing)에 대 한 컨트롤에 지원을 추가 합니다. 사용이 허가 된 컨트롤은 클라이언트 컴퓨터에 올바른 라이선스가 있는 경우에만 호스팅될 수 있습니다.

## <a name="see-also"></a>참고 항목

[ATL 컨트롤 마법사](../../atl/reference/atl-control-wizard.md)
