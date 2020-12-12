---
description: '자세히 알아보기: MFC ActiveX 컨트롤: 앰비언트 속성 액세스'
title: 'MFC ActiveX 컨트롤: 앰비언트 속성 액세스'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: 6b553c73873a6f96cab3ab55b576a51045c06609
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203070"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX 컨트롤: 앰비언트 속성 액세스

이 문서에서는 ActiveX 컨트롤이 해당 컨트롤 컨테이너의 앰비언트 속성에 액세스 하는 방법을 설명 합니다.

컨트롤은 컨테이너의 앰비언트 속성에 액세스 하 여 컨테이너에 대 한 정보를 가져올 수 있습니다. 이러한 속성은 컨테이너의 배경색, 컨테이너에서 사용 하는 현재 글꼴 및 현재 컨테이너가 사용자 모드 또는 디자이너 모드에 있는지 여부와 같은 작업 특성 등의 시각적 특성을 노출 합니다. 컨트롤은 앰비언트 속성을 사용 하 여 해당 모양 및 동작을 포함 된 특정 컨테이너에 맞게 조정할 수 있습니다. 그러나 컨트롤은 해당 컨테이너가 특정 앰비언트 속성을 지 원하는 것으로 가정해 서는 안 됩니다. 실제로 일부 컨테이너는 앰비언트 속성을 전혀 지원 하지 않을 수 있습니다. 앰비언트 속성이 없으면 컨트롤은 적절 한 기본값을 가정 해야 합니다.

앰비언트 속성에 액세스 하려면 [COleControl:: GetAmbientProperty](reference/colecontrol-class.md#getambientproperty)를 호출 합니다. 이 함수는 첫 번째 매개 변수 (파일 OLECTL)로 앰비언트 속성의 디스패치 ID를 예상 합니다. H는 앰비언트 속성의 표준 집합에 대 한 디스패치 Id를 정의 합니다.

함수의 매개 변수는 `GetAmbientProperty` 디스패치 ID, 예상 속성 유형을 나타내는 variant 태그 및 값이 반환 되어야 하는 메모리에 대 한 포인터입니다. 이 포인터가 참조 하는 데이터 형식은 variant 태그에 따라 달라 집니다. 이 함수는 컨테이너가 속성을 지 원하는 경우 **TRUE** 를 반환 하 고 그렇지 않으면 **FALSE** 를 반환 합니다.

다음 코드 예제에서는 "UserMode" 라는 앰비언트 속성의 값을 가져옵니다. 컨테이너에서이 속성을 지원 하지 않으면 기본값인 **TRUE** 로 가정 합니다.

[!code-cpp[NVC_MFC_AxUI#30](codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

사용자 편의를 위해에서는 `COleControl` 일반적으로 사용 되는 많은 앰비언트 속성에 액세스 하는 도우미 함수를 제공 하 고 속성을 사용할 수 없는 경우 적절 한 기본값을 반환 합니다. 이러한 도우미 함수는 다음과 같습니다.

- [COleControl::AmbientBackColor](reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  호출자 `Release( )` 는 반환 된 글꼴에 대해를 호출 해야 합니다.

- [AmbientForeColor](reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](reference/colecontrol-class.md#ambientshowgrabhandles)

앰비언트 속성의 값이 변경 되 면 (컨테이너의 일부 작업을 통해) `OnAmbientPropertyChanged` 컨트롤의 멤버 함수가 호출 됩니다. 이러한 알림을 처리 하려면이 멤버 함수를 재정의 합니다. 에 대 한 매개 변수는 `OnAmbientPropertyChanged` 영향을 받는 앰비언트 속성의 디스패치 ID입니다. 이 디스패치 ID 값은 하나 이상의 앰비언트 속성이 변경 되었음을 나타내는 DISPID_UNKNOWN 될 수 있지만 영향을 받는 속성에 대 한 정보는 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
