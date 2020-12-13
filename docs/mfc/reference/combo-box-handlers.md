---
description: '자세한 정보: 콤보 상자 처리기'
title: 콤보 상자 처리기
ms.date: 11/04/2016
f1_keywords:
- ON_CBN_KILLFOCUS
- ON_CBN_ERRSPACE
- ON_CBN_EDITCHANGE
- ON_CBN_CLOSEUP
- ON_CBN_DBLCLK
- ON_CBN_EDITUPDATE
- ON_CBN_DROPDOWN
- ON_CBN_SELENDOK
- ON_CBN_SELCHANGE
- ON_CBN_SETFOCUS
- ON_CBN_SELENDCANCEL
helpviewer_keywords:
- ON_CBN_CLOSEUP
- ON_CBN_SETFOCUS
- ON_CBN_DBLCLK
- ON_CBN_SELENDCANCEL
- ON_CBN_DROPDOWN
- ON_CBN_EDITUPDATE
- ON_CBN_KILLFOCUS
- combo boxes [MFC], handlers
- ON_CBN_EDITCHANGE
- ON_CBN_ERRSPACE
- ON_CBN_SELENDOK
- ON_CBN_SELCHANGE
ms.assetid: 7f092412-01b7-4242-95ec-41ba506b9d71
ms.openlocfilehash: 5d15e1db53d48c597ab0f47577746bfbc6790ad3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331376"
---
# <a name="combo-box-handlers"></a>콤보 상자 처리기

함수 프로토타입에 해당 하는 맵 항목은 다음과 같습니다.

|맵 항목|함수 프로토타입|
|---------------|------------------------|
|ON_CBN_CLOSEUP ( \<id> , \<memberFxn> )|afx_msg void memberFxn ()|
|ON_CBN_DBLCLK ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_DROPDOWN ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_EDITCHANGE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_EDITUPDATE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_ERRSPACE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_KILLFOCUS ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_SELCHANGE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_SELENDCANCEL ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_SELENDOK ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_CBN_SETFOCUS ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|

## <a name="see-also"></a>참고 항목

[메시지 맵](../../mfc/reference/message-maps-mfc.md)
