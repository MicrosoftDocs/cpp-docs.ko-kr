---
description: '자세한 정보: 콜백 항목 및 콜백 마스크'
title: 콜백 항목 및 콜백 마스크
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 0740afbee61f3173e2005fd927982c94786f03f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339763"
---
# <a name="callback-items-and-the-callback-mask"></a>콜백 항목 및 콜백 마스크

각 항목에 대해 목록 뷰 컨트롤은 일반적으로 레이블 텍스트, 항목 아이콘의 이미지 목록 인덱스 및 항목 상태에 대 한 비트 플래그 집합을 저장 합니다. 응용 프로그램에서 항목에 대 한 일부 정보를 이미 저장 한 경우에 유용한 콜백 항목으로 개별 항목을 정의할 수 있습니다.

구조체의 및 멤버에 적절 한 값을 지정 하 여 항목을 콜백 항목으로 정의 `pszText` `iImage` `LVITEM` 합니다 ( [CListCtrl:: GetItem](reference/clistctrl-class.md#getitem)참조). 응용 프로그램에서 항목의 또는 하위 항목의 텍스트를 유지 관리 하는 경우 멤버의 **LPSTR_TEXTCALLBACK** 값을 지정 합니다 `pszText` . 응용 프로그램에서 항목에 대 한 아이콘 추적을 유지 하는 경우 멤버의 **I_IMAGECALLBACK** 값을 지정 합니다 `iImage` .

콜백 항목을 정의 하는 것 외에도 컨트롤의 콜백 마스크를 수정할 수 있습니다. 이 마스크는 컨트롤이 아닌 응용 프로그램에서 현재 데이터를 저장 하는 항목 상태를 지정 하는 비트 플래그 집합입니다. 콜백 마스크는 특정 항목에 적용 되는 콜백 항목 지정과 달리 컨트롤의 모든 항목에 적용 됩니다. 콜백 마스크는 기본적으로 0입니다. 즉, 컨트롤이 모든 항목 상태를 추적 합니다. 이 기본 동작을 변경 하려면 다음 값을 조합 하 여 마스크를 초기화 합니다.

- **LVIS_CUT** 항목은 잘라내기 및 붙여넣기 작업으로 표시 됩니다.

- **LVIS_DROPHILITED** 항목이 끌어서 놓기 대상으로 강조 표시 됩니다.

- **LVIS_FOCUSED** 항목에 포커스가 있습니다.

- **LVIS_SELECTED** 항목이 선택 됩니다.

- **LVIS_OVERLAYMASK** 응용 프로그램은 각 항목에 대 한 현재 오버레이 이미지의 이미지 목록 인덱스를 저장 합니다.

- **LVIS_STATEIMAGEMASK** 응용 프로그램은 각 항목에 대 한 현재 상태 이미지의 이미지 목록 인덱스를 저장 합니다.

이 마스크를 검색 하 고 설정 하는 방법에 대 한 자세한 내용은 [CListCtrl:: getcallbackmask](reference/clistctrl-class.md#getcallbackmask) 및 [CListCtrl:: setcallbackmask](reference/clistctrl-class.md#setcallbackmask)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
