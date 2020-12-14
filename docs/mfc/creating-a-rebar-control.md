---
description: '자세한 정보: Rebar 컨트롤 만들기'
title: Rebar 컨트롤 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 71328af9d4701c412f7876629ebd2a56fa8ffd04
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310020"
---
# <a name="creating-a-rebar-control"></a>Rebar 컨트롤 만들기

[Cre바 ctrl](reference/crebarctrl-class.md) 개체는 부모 개체를 표시 하기 전에 만들어야 합니다. 이렇게 하면 그리기 문제가 발생할 가능성이 최소화됩니다.

예를 들어, rebar 컨트롤(프레임 창 개체에 사용)은 일반적으로 도구 모음 컨트롤에 대한 부모 창으로 사용됩니다. 따라서 rebar 컨트롤의 부모는 프레임 창 개체입니다. 프레임 창 개체가 부모이기 때문에, 해당 부모의 `OnCreate` 멤버 함수는 rebar 컨트롤을 생성하기 위한 최적의 위치입니다.

`CReBarCtrl` 개체를 사용하려면, 일반적으로 다음 단계를 수행해야 합니다.

### <a name="to-use-a-crebarctrl-object"></a>CReBarCtrl 개체를 사용하려면

1. [Cre바 ctrl](reference/crebarctrl-class.md) 개체를 구성 합니다.

1. [Create](reference/crebarctrl-class.md#create) 를 호출 하 여 Windows rebar 공용 컨트롤을 만들고 개체에 연결 하 여 `CReBarCtrl` 원하는 스타일을 지정 합니다.

1. Rebar 컨트롤 개체의 배경으로 사용할 [Cbitmap:: loadbitmap](reference/cbitmap-class.md#loadbitmap)에 대 한 호출을 사용 하 여 비트맵을 로드 합니다.

1. rebar 컨트롤 개체에 포함되는 모든 자식 창 개체(도구 모음, 대화 상자 컨트롤 등)를 만들고 초기화합니다.

1. 삽입할 대역에 대 한 필요한 정보를 사용 하 여 **Re바 밴드 정보** 구조를 초기화 합니다.

1. [Insertband](reference/crebarctrl-class.md#insertband) 을 호출 하 여 기존 자식 창 (예: `m_wndReToolBar` )을 새 rebar 컨트롤에 삽입 합니다. 기존 rebar 컨트롤에 밴드를 삽입 하는 방법에 대 한 자세한 내용은 [Rebar 컨트롤 및 밴드](rebar-controls-and-bands.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CReBarCtrl 사용](using-crebarctrl.md)<br/>
[컨트롤](controls-mfc.md)
