---
description: User-Defined 처리기에 대 한 자세한 정보
title: 사용자 정의 처리기
ms.date: 11/04/2016
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
ms.openlocfilehash: 8a3b7389d7388fb54ae39d3b1805594b64556652
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218526"
---
# <a name="user-defined-handlers"></a>사용자 정의 처리기

함수 프로토타입에 해당 하는 맵 항목은 다음과 같습니다.

|맵 항목|함수 프로토타입|
|---------------|------------------------|
|ON_MESSAGE ( \<message> , \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_MESSAGE ( \<nMessageVariable> , \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_THREAD_MESSAGE ( \<message> , \<memberFxn> )|afx_msg void memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable> , \<memberFxn> )|afx_msg void memberFxn (WPARAM, LPARAM);|

## <a name="see-also"></a>참고 항목

[메시지 맵](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 메시지에 대 한 처리기](../../mfc/reference/handlers-for-wm-messages.md)
