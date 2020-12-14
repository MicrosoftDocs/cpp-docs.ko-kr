---
description: '자세한 정보: ActiveX 컨트롤 컨테이너: 대화 상자가 아닌 컨테이너에서 컨트롤 사용'
title: 'ActiveX 컨트롤 컨테이너: 대화 상자가 아닌 컨테이너에서 컨트롤 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: 699f1faa5c88eb965a320c210de6e5e6c2ee94ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197675"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX 컨트롤 컨테이너: 대화 상자가 아닌 컨테이너에서 컨트롤 사용

SDI 또는 MDI 응용 프로그램과 같은 일부 응용 프로그램에서는 응용 프로그램의 창에 컨트롤을 포함 하는 것이 좋습니다. Visual C++으로 삽입 된 래퍼 클래스의 **Create** member 함수는 대화 상자 없이 동적으로 컨트롤의 인스턴스를 만들 수 있습니다.

**Create** member 함수에는 다음과 같은 매개 변수가 있습니다.

*lpszWindowName*<br/>
컨트롤의 Text 또는 Caption 속성 (있는 경우)에 표시 되는 텍스트에 대 한 포인터입니다.

*dwStyle*<br/>
Windows 스타일. 전체 목록은 [CWnd:: CreateControl](reference/cwnd-class.md#createcontrol)을 참조 하세요.

*rect*<br/>
컨트롤의 크기와 위치를 지정 합니다.

*pParentWnd*<br/>
컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . **NULL** 이 아니어야 합니다.

*nID*<br/>
컨트롤 ID를 지정 하 고 컨테이너에서 컨트롤을 참조 하는 데 사용할 수 있는 컨트롤 ID를 지정 합니다.

이 함수를 사용 하 여 동적으로 ActiveX 컨트롤을 만드는 한 가지 예는 SDI 응용 프로그램의 폼 보기입니다. 그런 다음 `WM_CREATE` 응용 프로그램의 처리기에서 컨트롤의 인스턴스를 만들 수 있습니다.

이 예제에서 `CMyView` 는 주 뷰 클래스이 고, `CCirc` 은 래퍼 클래스 이며,는 CIRC입니다. H는 헤더 (. H) 래퍼 클래스의 파일입니다.

이 기능을 구현 하는 과정은 네 단계로 구성 됩니다.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>대화 상자가 아닌 창에서 동적으로 ActiveX 컨트롤을 만들려면

1. CIRC를 삽입 합니다. CMYVIEW의 H. H는 클래스 정의 바로 앞에 `CMyView` 있습니다.

   [!code-cpp[NVC_MFC_AxCont#12](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. `CCirc`CMYVIEW에 있는 클래스 정의의 보호 된 섹션에 멤버 변수 (형식)를 추가 `CMyView` 합니다. 넣기

   [!code-cpp[NVC_MFC_AxCont#13](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. `WM_CREATE`클래스에 메시지 처리기를 추가 `CMyView` 합니다.

1. 처리기 함수에서 포인터를 `CMyView::OnCreate` `Create` 부모 창으로 사용 하 여 컨트롤의 함수를 호출 합니다 **`this`** .

   [!code-cpp[NVC_MFC_AxCont#15](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. 프로젝트를 다시 빌드합니다. 응용 프로그램의 뷰를 만들 때마다 Circ 컨트롤이 동적으로 생성 됩니다.

## <a name="see-also"></a>참고 항목

[ActiveX 컨트롤 컨테이너](activex-control-containers.md)
