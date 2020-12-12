---
description: '자세히 알아보기: 뷰에서 그리기'
title: 뷰에 그리기
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: b5d6b33d91f6a71048162078a926c5ad4336d6a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283409"
---
# <a name="drawing-in-a-view"></a>뷰에 그리기

응용 프로그램의 거의 모든 그리기 `OnDraw` 는 뷰 클래스에서 재정의 해야 하는 뷰의 멤버 함수에서 발생 합니다. ( [뷰를 통해 사용자 입력 해석](interpreting-user-input-through-a-view.md)에서 설명한 마우스 그리기는 예외입니다.) 사용자의 `OnDraw` 재정의:

1. 사용자가 제공 하는 문서 멤버 함수를 호출 하 여 데이터를 가져옵니다.

1. 프레임 워크가 전달 하는 장치 컨텍스트 개체의 멤버 함수를 호출 하 여 데이터를 표시 `OnDraw` 합니다.

문서 데이터가 변경 되 면 변경 내용을 반영 하기 위해 뷰를 다시 그려야 합니다. 일반적으로이는 사용자가 문서에 대 한 보기를 변경 하는 경우에 발생 합니다. 이 경우 뷰는 문서의 [UpdateAllViews](reference/cdocument-class.md#updateallviews) 멤버 함수를 호출 하 여 동일한 문서에 대 한 모든 보기를 자동으로 업데이트 합니다. `UpdateAllViews` 각 뷰의 [OnUpdate](reference/cview-class.md#onupdate) 멤버 함수를 호출 합니다. 의 기본 구현에서는 `OnUpdate` 뷰의 전체 클라이언트 영역을 무효화 합니다. 이를 재정의 하 여 문서의 수정 된 부분에 매핑되는 클라이언트 영역의 영역만 무효화할 수 있습니다.

`UpdateAllViews`클래스의 멤버 함수와 `CDocument` `OnUpdate` 클래스의 멤버 함수를 `CView` 사용 하면 문서에서 수정 된 부분을 설명 하는 정보를 전달할 수 있습니다. 이 "힌트" 메커니즘을 통해 뷰가 다시 그려야 하는 영역을 제한할 수 있습니다. `OnUpdate` 두 개의 "힌트" 인수를 사용 합니다. **LPARAM** 형식의 첫 번째 *lhint* 를 사용 하면 원하는 데이터를 전달할 수 있으며, * 형식의 두 번째, *phint* 를 사용 하 여 `CObject` 에서 파생 된 개체에 대 한 포인터를 전달할 수 있습니다 `CObject` .

뷰가 무효화 되 면 Windows에서 **WM_PAINT** 메시지를 보냅니다. 뷰의 [OnPaint](reference/cwnd-class.md#onpaint) handler 함수는 [CPaintDC](reference/cpaintdc-class.md) 클래스의 장치 컨텍스트 개체를 만들고 뷰의 멤버 함수를 호출 하 여 메시지에 응답 합니다 `OnDraw` . 일반적으로는 재정의 처리기 함수를 작성할 필요가 없습니다 `OnPaint` .

[장치 컨텍스트](device-contexts.md) 는 디스플레이 또는 프린터와 같은 장치의 그리기 특성에 대 한 정보를 포함 하는 Windows 데이터 구조입니다. 모든 그리기 호출은 장치 컨텍스트 개체를 통해 수행 됩니다. 화면에서 그리기의 경우 `OnDraw` 는 개체를 전달 `CPaintDC` 합니다. 프린터에 대 한 그리기의 경우 현재 프린터에 대해 설정 된 [CDC](reference/cdc-class.md) 개체가 전달 됩니다.

뷰에서 그리기 위한 코드는 먼저 문서에 대 한 포인터를 검색 한 다음 장치 컨텍스트를 통해 그리기 호출을 수행 합니다. 다음의 간단한 `OnDraw` 예제에서는이 프로세스를 보여 줍니다.

[!code-cpp[NVC_MFCDocView#1](codesnippet/cpp/drawing-in-a-view_1.cpp)]

이 예제에서는 `GetData` 함수를 파생 문서 클래스의 멤버로 정의 합니다.

이 예제에서는 문서에서 가져온 모든 문자열을 뷰의 가운데에 인쇄 합니다. `OnDraw`화면 그리기를 위해 호출 하는 경우 `CDC` *pDC* 에 전달 된 개체는 해당 `CPaintDC` 생성자가 이미 호출 된입니다 `BeginPaint` . 그리기 함수 호출은 장치 컨텍스트 포인터를 통해 수행 됩니다. 장치 컨텍스트 및 그리기 호출에 대 한 자세한 내용은 *MFC 참조* 의 [CDC](reference/cdc-class.md) 클래스 및 [창 개체 작업](working-with-window-objects.md)을 참조 하세요.

을 작성 하는 방법에 대 한 자세한 예제 `OnDraw` 는 [MFC 샘플](../overview/visual-cpp-samples.md#mfc-samples)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[뷰 사용](using-views.md)
