---
description: '자세히 알아보기: Slider 컨트롤 멤버 함수'
title: 슬라이더 컨트롤 멤버 함수
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
ms.openlocfilehash: 57108872a779bc4876be89afd5b81008f69a0837
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216901"
---
# <a name="slider-control-member-functions"></a>슬라이더 컨트롤 멤버 함수

응용 프로그램은 slider 컨트롤의 멤버 함수를 호출 하 여 slider 컨트롤 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md))에 대 한 정보를 검색 하 고 해당 특성을 변경할 수 있습니다.

슬라이더의 위치 (즉, 사용자가 선택한 값)를 검색 하려면 [GetPos](../mfc/reference/csliderctrl-class.md#getpos) 멤버 함수를 사용 합니다. 슬라이더의 위치를 설정 하려면 [Setpos](../mfc/reference/csliderctrl-class.md#setpos) 멤버 함수를 사용 합니다. 언제 든 지 멤버 함수를 사용 `VerifyPos` 하 여 슬라이더가 최소값과 최 댓 값 사이에 있는지 확인할 수 있습니다.

슬라이더 컨트롤의 범위는 슬라이더 컨트롤에서 나타낼 수 있는 연속 값의 집합입니다. 대부분의 응용 프로그램 [은 first 멤버 함수](../mfc/reference/csliderctrl-class.md#setrange) 를 사용 하 여 처음 생성 될 때 slider 컨트롤의 범위를 설정 합니다. 응용 프로그램은 [SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) 및 [Setrangemin](../mfc/reference/csliderctrl-class.md#setrangemin) 멤버 함수를 사용 하 여 슬라이더 컨트롤이 생성 된 후 범위를 동적으로 변경할 수 있습니다. 범위가 동적으로 변경 될 수 있도록 하는 응용 프로그램은 일반적으로 사용자가 슬라이더 컨트롤 작업을 완료 했을 때 최종 범위 설정을 검색 합니다. 이러한 설정을 검색 하려면 [Getrange](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax)및 [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) 멤버 함수를 사용 합니다.

응용 프로그램은 TBS_AUTOTICKS 스타일을 사용 하 여 슬라이더 컨트롤의 눈금 표시를 자동으로 표시할 수 있습니다. 그러나 응용 프로그램에서 눈금 표시의 위치 또는 빈도를 제어 해야 하는 경우 여러 멤버 함수를 사용할 수 있습니다.

눈금 표시의 위치를 설정 하기 위해 응용 프로그램은 [Settic](../mfc/reference/csliderctrl-class.md#settic) 멤버 함수를 사용할 수 있습니다. [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) 멤버 함수를 사용 하면 응용 프로그램에서 슬라이더 컨트롤의 범위에서 일정 한 간격으로 표시 되는 눈금 표시를 설정할 수 있습니다. 예를 들어 응용 프로그램에서는이 멤버 함수를 사용 하 여 1 ~ 100 범위에서 10 개의 눈금 표시만 표시할 수 있습니다.

눈금 표시에 해당 하는 범위의 인덱스를 검색 하려면 [GetTic](../mfc/reference/csliderctrl-class.md#gettic) 멤버 함수를 사용 합니다. [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) 멤버 함수는 이러한 인덱스의 배열을 검색 합니다. 눈금 표시의 위치를 클라이언트 좌표로 검색 하려면 [GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) 멤버 함수를 사용 합니다. 응용 프로그램은 [GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) 멤버 함수를 사용 하 여 눈금 표시의 수를 검색할 수 있습니다.

[ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) member 함수는 슬라이더 컨트롤의 눈금 표시를 모두 제거 합니다.

슬라이더 컨트롤의 선 크기는 응용 프로그램이 TB_LINEDOWN 또는 TB_LINEUP 알림 메시지를 받을 때 슬라이더가 이동 하는 정도를 결정 합니다. 마찬가지로 페이지 크기는 TB_PAGEDOWN 및 TB_PAGEUP 알림 메시지에 대 한 응답을 결정 합니다. 응용 프로그램은 [Getlinesize](../mfc/reference/csliderctrl-class.md#getlinesize), [setlinesize](../mfc/reference/csliderctrl-class.md#setlinesize), [getpagesize](../mfc/reference/csliderctrl-class.md#getpagesize)및 [setpagesize](../mfc/reference/csliderctrl-class.md#setpagesize) 멤버 함수를 사용 하 여 줄 및 페이지 크기 값을 검색 하 고 설정할 수 있습니다.

응용 프로그램은 멤버 함수를 사용 하 여 슬라이더 컨트롤의 크기를 검색할 수 있습니다. [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) 멤버 함수는 슬라이더의 경계 사각형을 검색 합니다. [Getchannelrect](../mfc/reference/csliderctrl-class.md#getchannelrect) 멤버 함수는 슬라이더 컨트롤의 채널에 대 한 경계 사각형을 검색 합니다. 채널은 슬라이더가 이동 하는 영역이 며 범위를 선택할 때 강조 표시를 포함 합니다.

슬라이더 컨트롤에 TBS_ENABLESELRANGE 스타일이 있는 경우 사용자는 해당 컨트롤에서 연속 된 값의 범위를 선택할 수 있습니다. 여러 멤버 함수를 사용 하 여 선택 범위를 동적으로 조정할 수 있습니다. [Setselection](../mfc/reference/csliderctrl-class.md#setselection) 멤버 함수는 선택 항목의 시작 및 끝 위치를 설정 합니다. 사용자가 선택 범위를 설정 하는 작업이 완료 되 면 응용 프로그램은 [Getselection](../mfc/reference/csliderctrl-class.md#getselection) 멤버 함수를 사용 하 여 설정을 검색할 수 있습니다. 사용자의 선택을 지우려면 [Clearsel](../mfc/reference/csliderctrl-class.md#clearsel) 멤버 함수를 사용 합니다.

## <a name="see-also"></a>참고 항목

[CSliderCtrl 사용](../mfc/using-csliderctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
