---
description: '자세한 정보: 방법: 코드에서 추적 구현'
title: '방법: 코드에서 추적 구현'
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 1b9211978c6ba5169a2d55e272b7e3ddf0678fd6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330210"
---
# <a name="how-to-implement-tracking-in-your-code"></a>방법: 코드에서 추적 구현

OLE 항목을 추적 하려면 항목을 클릭 하거나 문서 보기를 업데이트 하는 등 항목과 관련 된 특정 이벤트를 처리 해야 합니다. 모든 경우에서 임시 [CRectTracker](reference/crecttracker-class.md) 개체를 선언 하 고이 개체를 통해 항목을 조작 하는 것은 충분 합니다.

사용자가 항목을 선택 하거나 메뉴 명령을 사용 하 여 개체를 삽입 하는 경우 적절 한 스타일을 사용 하 여 추적기를 초기화 하 여 OLE 항목의 상태를 표시 해야 합니다. 다음 표에서는 OCLIENT 샘플에서 사용 되는 규칙을 간략하게 설명 합니다. 이러한 스타일에 대 한 자세한 내용은을 참조 하십시오 `CRectTracker` .

### <a name="container-styles-and-states-of-the-ole-item"></a>OLE 항목의 컨테이너 스타일 및 상태

|표시 된 스타일|OLE 항목의 상태입니다.|
|---------------------|-----------------------|
|점선 테두리|항목이 연결 되어 있습니다.|
|실선 테두리|항목이 문서에 포함 되어 있습니다.|
|크기 조정 핸들|항목이 현재 선택 되어 있습니다.|
|해치 테두리|항목이 현재 활성 상태입니다.|
|해칭 패턴 오버레이 항목|항목의 서버가 열려 있습니다.|

OLE 항목의 상태를 확인 하 고 적절 한 스타일을 설정 하는 프로시저를 사용 하 여이 초기화를 쉽게 처리할 수 있습니다. `SetupTracker`OCLIENT 샘플에 있는 함수는 추적기 초기화를 보여 줍니다. 이 함수에 대 한 매개 변수는 tracker ( *ptracker*;)의 주소입니다. tracker와 관련 된 클라이언트 항목에 대 한 포인터입니다. *Pitem*; *pTrueRect* 사각형에 대 한 포인터입니다. 이 함수의 전체 예제는 MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md)를 참조 하세요.

**Setuptracker** 코드 예제는 단일 함수를 제공 합니다. 함수의 줄은 함수의 기능에 대 한 설명과 함께 제공 됩니다.

[!code-cpp[NVC_MFCOClient#1](codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

추적기는 최소 크기를 설정 하 고 추적기의 스타일을 지워 초기화 됩니다.

[!code-cpp[NVC_MFCOClient#2](codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

다음 줄에서는 항목이 현재 선택 되어 있는지와 항목이 문서에 연결 되어 있는지, 아니면 포함 되어 있는지를 확인 합니다. 테두리 안쪽의에 있는 크기 조정 핸들은 해당 항목이 현재 선택 되어 있음을 나타내는 스타일에 추가 됩니다. 항목이 문서에 연결 된 경우 점선 테두리 스타일이 사용 됩니다. 항목이 포함 된 경우 실선 테두리를 사용 합니다.

[!code-cpp[NVC_MFCOClient#3](codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

항목이 현재 열려 있는 경우 다음 코드는 빗살 무늬 패턴으로 항목을 중첩 합니다.

[!code-cpp[NVC_MFCOClient#4](codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

그런 다음 추적기를 표시 해야 할 때마다이 함수를 호출할 수 있습니다. 예를 들어 `OnDraw` 뷰 클래스의 함수에서이 함수를 호출 합니다. 그러면 뷰를 다시 그릴 때마다 추적기의 모양이 업데이트 됩니다. 전체 예제는 `CMainView::OnDraw` MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md)의 함수를 참조 하세요.

응용 프로그램에서 추적 코드를 요구 하는 이벤트 (예: 크기 조정, 이동 또는 적중 검색)가 발생 합니다. 이러한 작업은 일반적으로 항목을 가져오거나 이동 하려고 시도 하는 것을 의미 합니다. 이러한 경우 크기 조정 핸들 또는 크기 조정 핸들 사이의 테두리 일부 중 어떤 것을 grabbed 결정 해야 합니다. `OnLButtonDown`메시지 처리기는 항목과 관련 하 여 마우스의 위치를 테스트 하는 데 적합 한 위치입니다. 을 호출 `CRectTracker::HitTest` 합니다. 테스트에서 이외의 `CRectTracker::hitOutside` 항목을 반환 하면 항목의 크기를 조정 하거나 이동 하는 것입니다. 따라서 멤버 함수에 대 한 호출을 수행 해야 `Track` 합니다. `CMainView::OnLButtonDown`전체 예제는 MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 에 있는 함수를 참조 하세요.

`CRectTracker`클래스는 이동, 크기 조정 또는 끌기 작업이 수행 되는지 여부를 나타내는 데 사용 되는 여러 커서 셰이프를 제공 합니다. 이 이벤트를 처리 하려면 현재 마우스 아래에 있는 항목이 선택 되어 있는지 확인 하십시오. 이면를 호출 `CRectTracker::SetCursor` 하거나 기본 처리기를 호출 합니다. 다음 예제는 MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md)에서 가져온 것입니다.

[!code-cpp[NVC_MFCOClient#5](codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>참고 항목

[추적기: OLE 응용 프로그램에서 추적기 구현](trackers-implementing-trackers-in-your-ole-application.md)
