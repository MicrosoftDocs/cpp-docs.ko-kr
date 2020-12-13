---
description: '자세히 알아보기: Rich Edit 컨트롤 무제한'
title: 바닥 없는 Rich Edit 컨트롤
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: ad3f78fb4a5e172c16faf3421b6a9da91d422888
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339815"
---
# <a name="bottomless-rich-edit-controls"></a>바닥 없는 Rich Edit 컨트롤

응용 프로그램은 필요에 따라 rich edit 컨트롤 ([CRichEditCtrl](reference/cricheditctrl-class.md))의 크기를 조정 하 여 항상 콘텐츠와 크기가 같도록 할 수 있습니다. Rich edit 컨트롤은 해당 콘텐츠 크기가 변경 될 때마다 [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) 알림 메시지를 부모 창으로 전송 하 여 "무제한" 기능 이라고 하는이를 지원 합니다.

**EN_REQUESTRESIZE** 알림 메시지를 처리할 때 응용 프로그램은 지정 된 [REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize) 구조체의 차원에 맞게 컨트롤의 크기를 조정 해야 합니다. 애플리케이션은 높이에서의 컨트롤 변경 사항을 수용하기 위해 컨트롤 근처의 모든 정보를 이동할 수 있습니다. 컨트롤의 크기를 조정 하려면 `CWnd` [Setwindowpos](reference/cwnd-class.md#setwindowpos)함수를 사용 하면 됩니다.

무제한 rich edit 컨트롤에서 [Requestresize](reference/cricheditctrl-class.md#requestresize) 멤버 함수를 사용 하 여 **EN_REQUESTRESIZE** 알림 메시지를 보내도록 강제할 수 있습니다. 이 메시지는 [Onsize](reference/cwnd-class.md#onsize) 처리기에서 유용할 수 있습니다.

**EN_REQUESTRESIZE** 알림 메시지를 받으려면 멤버 함수를 사용 하 여 알림을 사용 하도록 설정 해야 합니다 `SetEventMask` .

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](using-cricheditctrl.md)<br/>
[컨트롤](controls-mfc.md)
