---
description: '자세히 알아보기: CToolBarCtrl 개체 만들기'
title: CToolBarCtrl 개체 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: 2ea6f1c170fd82a18d4ceb9d5ca9e7fbadfcdbc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310111"
---
# <a name="creating-a-ctoolbarctrl-object"></a>CToolBarCtrl 개체 만들기

[CToolBarCtrl](reference/ctoolbarctrl-class.md) 개체에는 단추 이미지 비트맵 목록, 단추 레이블 문자열 목록 및 구조 목록 등의 여러 내부 데이터 구조가 포함 되어 `TBBUTTON` 있습니다 .이는 이미지 및/또는 문자열을 단추의 위치, 스타일, 상태 및 명령 ID와 연결 합니다. 이러한 데이터 구조의 각 요소는 0부터 시작 하는 인덱스를 참조 합니다. 개체를 사용 하려면 먼저 `CToolBarCtrl` 이러한 데이터 구조를 설정 해야 합니다. 데이터 구조 목록은 Windows SDK [도구 모음 컨트롤](controls-mfc.md) 을 참조 하세요. 문자열 목록은 단추 레이블에만 사용할 수 있습니다. 도구 모음에서 문자열을 검색할 수 없습니다.

`CToolBarCtrl` 개체를 사용하려면, 일반적으로 다음 단계를 수행해야 합니다.

### <a name="to-use-a-ctoolbarctrl-object"></a>CToolBarCtrl 개체를 사용 하려면

1. [CToolBarCtrl](reference/ctoolbarctrl-class.md) 개체를 생성 합니다.

1. [Create](reference/ctoolbarctrl-class.md#create) 를 호출 하 여 Windows 도구 모음 공용 컨트롤을 만들고 개체에 연결 `CToolBarCtrl` 합니다. 단추에 비트맵 이미지를 만들려면 [Addbitmap](reference/ctoolbarctrl-class.md#addbitmap)을 호출 하 여 도구 모음에 단추 비트맵을 추가 합니다. 단추에 대 한 문자열 레이블을 만들려면 [Addstring](reference/ctoolbarctrl-class.md#addstring) 및/또는 [addstring](reference/ctoolbarctrl-class.md#addstrings)를 호출 하 여 도구 모음에 문자열을 추가 합니다. `AddString`및/또는를 호출한 후에 `AddStrings` 는 [AutoSize](reference/ctoolbarctrl-class.md#autosize) 를 호출 하 여 문자열 또는 문자열이 표시 되도록 해야 합니다.

1. [Addbuttons](reference/ctoolbarctrl-class.md#addbuttons)를 호출 하 여 도구 모음에 단추 구조를 추가 합니다.

1. 도구 설명이 필요한 경우 도구 [설명 알림 처리](handling-tool-tip-notifications.md)의 설명에 따라 도구 모음의 소유자 창에서 **TTN_NEEDTEXT** 메시지를 처리 합니다.

1. 사용자가 도구 모음을 사용자 지정할 수 있도록 하려면 사용자 [지정 알림 처리](handling-customization-notifications.md)에 설명 된 대로 소유자 창에서 사용자 지정 알림 메시지를 처리 합니다.

## <a name="see-also"></a>참고 항목

[CToolBarCtrl 사용](using-ctoolbarctrl.md)<br/>
[컨트롤](controls-mfc.md)
