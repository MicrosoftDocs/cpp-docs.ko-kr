---
description: '자세한 정보: MFC ActiveX 컨트롤: 최적화'
title: 'MFC ActiveX 컨트롤: 최적화'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
ms.openlocfilehash: db7fc1f1bdcdc3a3ffbf3b14d1809806389f0862
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294108"
---
# <a name="mfc-activex-controls-optimization"></a>MFC ActiveX 컨트롤: 최적화

이 문서에서는 성능 향상을 위해 ActiveX 컨트롤을 최적화 하는 데 사용할 수 있는 기술을 설명 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

비활성 상태일 [때 활성화 옵션을 해제](turning-off-the-activate-when-visible-option.md) 하 고 [마우스 상호 작용을 제공](providing-mouse-interaction-while-inactive.md) 하는 항목은 활성화 될 때까지 창을 만들지 않는 컨트롤을 설명 합니다. 창 없는 [활성화를 제공 하](providing-windowless-activation.md) 는 항목에서는 창을 활성화 하는 경우에도 창을 만들지 않는 컨트롤에 대해 설명 합니다.

Windows에는 OLE 개체에 대 한 두 가지 주요 단점이 있습니다. 이러한 개체는 개체가 활성 상태일 때 투명 하거나 사각형이 아닌 것을 방지 하 고 컨트롤의 인스턴스화 및 표시에 대 한 큰 오버 헤드를 추가 합니다. 일반적으로 창을 만들 때 컨트롤의 작성 시간에는 60%가 소요 됩니다. 단일 공유 창 (일반적으로 컨테이너의) 및 일부 디스패치 코드를 사용 하는 경우 컨트롤은 일반적으로 성능 손실 없이 동일한 창 서비스를 받습니다. 창에는 대개 개체에 불필요 한 오버 헤드가 발생 합니다.

일부 최적화는 컨트롤이 특정 컨테이너에서 사용 되는 경우 성능을 향상 시 키 지 않습니다. 예를 들어 1996 이전에 릴리스된 컨테이너는 창 없는 활성화를 지원 하지 않으므로이 기능을 구현 해도 이전 컨테이너의 혜택은 제공 되지 않습니다. 그러나 거의 모든 컨테이너는 지 속성을 지원 하므로 컨트롤의 지 속성 코드를 최적화 하면 모든 컨테이너에서 성능이 향상 될 수 있습니다. 특정 컨테이너 형식에 맞게 컨트롤을 사용 하려면 해당 컨테이너에서 지원 되는 최적화를 조사할 수 있습니다. 그러나 일반적으로 다양 한 컨테이너를 사용할 수 있을 뿐만 아니라 컨트롤이 수행 되도록 특정 컨트롤에 적용할 수 있는 많은 기술을 구현 하려고 합니다.

[MFC ActiveX 컨트롤 마법사](reference/mfc-activex-control-wizard.md)의 [컨트롤 설정](reference/control-settings-mfc-activex-control-wizard.md) 페이지에서 이러한 최적화를 여러 개 구현할 수 있습니다.

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC ActiveX 컨트롤 마법사 OLE 최적화 옵션

|MFC ActiveX 컨트롤 마법사의 컨트롤 설정|작업|추가 정보|
|-------------------------------------------------------|------------|----------------------|
|**표시 될 때 활성화** 확인란|지우기|[표시 될 때 활성화 옵션 해제](turning-off-the-activate-when-visible-option.md)|
|**창 없는 활성화** 확인란|선택|[창 없는 활성화 제공](providing-windowless-activation.md)|
|**잘리지 않는 장치 컨텍스트** 확인란|선택|[잘리지 않는 장치 컨텍스트 사용](using-an-unclipped-device-context.md)|
|**깜빡임 없는 활성화** 확인란|선택|[Flicker-Free 활성화 제공](providing-flicker-free-activation.md)|
|**비활성 상태인 경우 마우스 포인터 알림** 확인란|선택|[비활성 상태에서 마우스 상호 작용 제공](providing-mouse-interaction-while-inactive.md)|
|**최적화 된 그리기 코드** 확인란|선택|[컨트롤 그리기 최적화](optimizing-control-drawing.md)|

이러한 최적화를 구현 하는 멤버 함수에 대 한 자세한 내용은 [COleControl](reference/colecontrol-class.md)을 참조 하십시오.

자세한 내용은 다음을 참조하세요.

- [지 속성 및 초기화 최적화](optimizing-persistence-and-initialization.md)

- [창 없는 활성화 제공](providing-windowless-activation.md)

- [표시 될 때 활성화 옵션 해제](turning-off-the-activate-when-visible-option.md)

- [비활성 상태에서 마우스 상호 작용 제공](providing-mouse-interaction-while-inactive.md)

- [Flicker-Free 활성화 제공](providing-flicker-free-activation.md)

- [잘리지 않는 장치 컨텍스트 사용](using-an-unclipped-device-context.md)

- [컨트롤 그리기 최적화](optimizing-control-drawing.md)

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
