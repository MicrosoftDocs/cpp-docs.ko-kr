---
title: '방법: 리본 컨트롤 및 이벤트 처리기 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 7f5b85fad181dba147c2135784d237bccdceb422
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637998"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>방법: 리본 컨트롤 및 이벤트 처리기 추가

리본 컨트롤은 단추 및 패널에 추가한 콤보 상자와 같은 요소입니다. 패널은 관련된 컨트롤 그룹을 표시 하는 리본 표시줄의 영역입니다.

이 항목에서는 리본 디자이너를 열고, 추가 단추를 하 고 "Hello World"를 표시 하는 이벤트를 연결 합니다.

### <a name="to-open-the-ribbon-designer"></a>리본 디자이너를 열려면

1. Visual Studio에서에 **뷰** 메뉴에서 클릭 **리소스 뷰**합니다.

1. **리소스 뷰**, 디자인 화면에 표시할 리본 리소스를 두 번 클릭 합니다.

### <a name="to-add-a-button-and-an-event-handler"></a>단추 및 이벤트 처리기를 추가 하려면

1. **도구 모음**, 클릭 **단추** 의 디자인 화면에 놓습니다.

1. 단추를 마우스 오른쪽 단추로 클릭 하 고 클릭 **이벤트 처리기 추가**합니다.

1. 에 **이벤트 처리기 마법사**에서 기본 설정을 확인 하 고 클릭 **추가 하 고 편집**합니다. 자세한 내용은 [이벤트 처리기 마법사](../ide/event-handler-wizard.md)합니다.

1. 코드 편집기에서 다음 코드를 처리기 함수에 추가 합니다.

```
    MessageBox((LPCTSTR)L"Hello World");

```

## <a name="see-also"></a>참고 항목

[RibbonGadgets 샘플: 리본 가젯 응용 프로그램](../visual-cpp-samples.md)<br/>
[리본 디자이너(MFC)](../mfc/ribbon-designer-mfc.md)

