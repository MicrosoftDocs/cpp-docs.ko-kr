---
description: '자세히 알아보기: Rich Edit 컨트롤에서 인쇄'
title: Rich Edit 컨트롤의 인쇄
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 9b5c272df36c6a4472c82cc4b0655b1d9626c2ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205735"
---
# <a name="printing-in-rich-edit-controls"></a>Rich Edit 컨트롤의 인쇄

프린터와 같이 지정 된 장치에 대 한 출력을 렌더링 하도록 rich edit 컨트롤 ([CRichEditCtrl](reference/cricheditctrl-class.md))에 지시할 수 있습니다. Rich edit 컨트롤에서 텍스트의 서식을 지정 하는 출력 장치를 지정할 수도 있습니다.

특정 장치에 대해 rich edit 컨트롤 내용의 일부를 서식 지정 하려면 [Formatrange](reference/cricheditctrl-class.md#formatrange) 멤버 함수를 사용할 수 있습니다. 이 함수와 함께 사용 되는 [Formatrange](/windows/win32/api/richedit/ns-richedit-formatrange) 구조는 대상 장치의 DC (장치 컨텍스트) 뿐만 아니라 포맷할 텍스트 범위를 지정 합니다.

출력 장치에 대 한 텍스트의 서식을 지정 하 고 나면 [Displayband](reference/cricheditctrl-class.md#displayband) 멤버 함수를 사용 하 여 출력을 장치로 보낼 수 있습니다. 및를 반복적으로 사용 하 여 `FormatRange` `DisplayBand` rich edit 컨트롤의 콘텐츠를 인쇄 하는 응용 프로그램에서 줄무늬를 구현할 수 있습니다. 줄무늬는 인쇄를 위해 출력을 더 작은 부분으로 나눕니다.

[SetTargetDevice](reference/cricheditctrl-class.md#settargetdevice) 멤버 함수를 사용 하 여 서식 있는 편집 컨트롤에서 텍스트의 서식을 지정 하는 대상 장치를 지정할 수 있습니다. 이 함수는 WYSIWYG (표시 되는 내용) 서식 지정에 유용 합니다 .이 경우 응용 프로그램은 화면 대신 기본 프린터의 글꼴 메트릭을 사용 하 여 텍스트를 배치 합니다.

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](using-cricheditctrl.md)<br/>
[컨트롤](controls-mfc.md)
