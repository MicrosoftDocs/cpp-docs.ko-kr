---
title: '방법: 리본 컨트롤 및 이벤트 처리기 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: d6382c8ebf73fe7a26b3950cc1965b229c22dbb7
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501232"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>방법: 리본 컨트롤 및 이벤트 처리기 추가

리본 컨트롤은 패널에 추가 하는 단추 및 콤보 상자와 같은 요소입니다. 패널은 관련 컨트롤 그룹을 표시 하는 리본 표시줄의 영역입니다.

이 항목에서는 리본 디자이너를 열고 단추를 추가한 다음 "Hello World"를 표시 하는 이벤트를 연결 합니다.

### <a name="to-open-the-ribbon-designer"></a>리본 디자이너를 열려면

1. Visual Studio의 **보기** 메뉴에서 **리소스 뷰**를 클릭 합니다.

1. **리소스 뷰**에서 리본 리소스를 두 번 클릭 하 여 디자인 화면에 표시 합니다.

### <a name="to-add-a-button-and-an-event-handler"></a>단추 및 이벤트 처리기를 추가 하려면

1. **도구 모음**에서 **단추** 를 클릭 하 여 디자인 화면의 패널로 끌어 놓습니다.

1. 단추를 마우스 오른쪽 단추로 클릭 하 고 **이벤트 처리기 추가**를 클릭 합니다.

1. **이벤트 처리기 마법사**에서 기본 설정을 확인 하 고 **추가 및 편집**을 클릭 합니다. 자세한 내용은 [이벤트 처리기 마법사](../ide/adding-an-event-handler-visual-cpp.md#event-handler-wizard)를 참조 하십시오.

1. 코드 편집기에서 다음 코드를 처리기 함수에 추가 합니다.

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>참고 항목

[보려면 ribbongadgets 샘플: 리본 가젯 응용 프로그램](../overview/visual-cpp-samples.md)<br/>
[리본 디자이너 (MFC)](ribbon-designer-mfc.md)
