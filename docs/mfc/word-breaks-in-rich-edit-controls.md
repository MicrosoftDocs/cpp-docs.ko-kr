---
description: '자세히 알아보기: Rich Edit 컨트롤의 단어 분리'
title: Rich Edit 컨트롤의 단어 분리
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: 662a6b8441c4a9041a539acdabcab74f12d52782
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172715"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Rich Edit 컨트롤의 단어 분리

Rich edit 컨트롤 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))은 "단어 분리 프로시저" 라는 함수를 호출 하 여 단어 사이의 나누기를 찾고 줄을 나눌 수 있는 위치를 결정 합니다. 컨트롤은 자동 줄 바꿈 작업을 수행할 때와 CTRL + LEFT 및 CTRL + RIGHT 키 조합을 처리할 때이 정보를 사용 합니다. 응용 프로그램은 rich edit 컨트롤에 메시지를 보내 기본 단어 중단 프로시저를 대체 하 고, 단어 분리 정보를 검색 하 고, 지정 된 문자가 속하는 줄을 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](../mfc/using-cricheditctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
