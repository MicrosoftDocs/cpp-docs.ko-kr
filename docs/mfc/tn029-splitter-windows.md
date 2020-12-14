---
description: '자세히 알아보기: TN029: 분할자 창'
title: 'TN029: 분할 창'
ms.date: 11/04/2016
f1_keywords:
- vc.windows.splitter
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
ms.openlocfilehash: e1079adf403b64aa47f5aae00aa32f7da702ddcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215640"
---
# <a name="tn029-splitter-windows"></a>TN029: 분할 창

이 참고는 창 분할을 제공 하 고 다른 창 창의 크기 조정을 관리 하는 MFC [CSplitterWnd 클래스](../mfc/reference/csplitterwnd-class.md)에 대해 설명 합니다.

## <a name="splitter-styles"></a>분할자 스타일

에서는 `CSplitterWnd` 두 가지 분할 창 스타일을 지원 합니다.

"정적 분할자"에서는 분할자 창이 만들어질 때 창을 만듭니다. 창의 순서와 수는 변경 되지 않습니다. 분할자 막대는 서로 다른 창의 크기를 조정 하는 데 사용 됩니다. 이 스타일을 사용 하 여 각 창에 다른 뷰 클래스를 표시할 수 있습니다. 이 분할자 스타일을 사용 하는 프로그램의 예로는 Visual C++ 그래픽 편집기와 Windows 파일 관리자가 있습니다. 분할자 창의이 스타일은 분할자 상자를 사용 하지 않습니다.

"동적 분할 영역"에서는 사용자가 새 보기를 분할 및 분할 취소 하는 동안 추가 창이 만들어지고 제거 됩니다. 이 분할자는 단일 뷰로 시작 하 고 분할을 시작 하는 사용자에 게 분할자 상자를 제공 합니다. 분할 창은 뷰가 한 방향으로 분할 될 때 새 뷰 개체를 동적으로 만듭니다. 새 뷰 개체는 새 창을 나타냅니다. 뷰가 키보드 인터페이스를 사용 하 여 양방향으로 분할 된 경우 분할자 창에서는 세 개의 새 창에 대해 세 개의 새 뷰 개체를 만듭니다. 분할이 활성화 되어 있는 동안 창에서 분할자 상자를 분할자 막대로 표시 합니다. 사용자가 분할을 제거 하면 Windows에서 추가 뷰 개체를 소멸 하지만 분할 창이 소멸 될 때까지 원래 뷰가 남아 있습니다. Microsoft Excel 및 Microsoft Word는 dynamic splitter 스타일을 사용 하는 응용 프로그램의 예입니다.

두 종류의 분할자 창을 만들 때 분할자에서 관리할 최대 행 및 열 수를 지정 해야 합니다. 정적 분할자는 모든 행과 열을 채우는 창을 만듭니다. 동적 분할자는가 만들어질 때 첫 번째 창만 만듭니다 `CSplitterWnd` .

정적 분할자에 대해 지정할 수 있는 최대 창 수는 16 개의 행으로 된 열입니다. 권장 구성은 다음과 같습니다.

- 1 행 x 2 열 (일반적으로 서로 다른 창 포함)

- 2 행 x 1 열: 일반적으로 서로 다른 창이 있는 경우

- 2 행 x 2 열: 일반적으로 비슷한 창이 있습니다.

동적 분할자에 대해 지정할 수 있는 최대 창 수는 2 개 열로 된 행입니다. 권장 구성은 다음과 같습니다.

- 1 행 x 2 열: 열 형식 데이터의 경우

- 2 행 x 1 열: 텍스트 또는 기타 데이터의 경우

- 2 행 x 2 열: 그리드 또는 테이블 지향 데이터

## <a name="splitter-examples"></a>분할자 예

대부분의 MFC 샘플 프로그램에서는 분할자 창을 직접 또는 간접적으로 사용 합니다. MFC 일반 샘플 [VIEWEX](../overview/visual-cpp-samples.md) 는 분할자에 분할자를 추가 하는 방법을 비롯 하 여 정적 분할자의 여러 사용을 보여 줍니다.

또한 클래스 마법사를 사용 하 여 분할자 창이 포함 된 새 MDI (다중 문서 인터페이스) 자식 프레임 창 클래스를 만들 수 있습니다. 분할자 창에 대 한 자세한 내용은 [여러 문서 형식, 뷰 및 프레임 창](../mfc/multiple-document-types-views-and-frame-windows.md)을 참조 하세요.

## <a name="terminology-used-by-implementation"></a>구현에 사용 되는 용어

다음은 분할자 창과 관련 된 용어 목록입니다.

`CSplitterWnd`: 행 또는 열의 모든 창 간에 공유 되는 창 분할 컨트롤 및 스크롤 막대를 제공 하는 창입니다. 0부터 시작 하는 숫자를 사용 하 여 행과 열을 지정 합니다. 첫 번째 창은 row = 0 및 column = 0입니다.

Pane:에서 관리 하는 응용 프로그램 관련 창 `CSplitterWnd` 입니다. 창은 일반적으로 [CView 클래스](../mfc/reference/cview-class.md)에서 파생 되는 개체 이지만 적절 한 자식 창 ID가 있는 모든 [CWnd](../mfc/reference/cwnd-class.md) 개체가 될 수 있습니다.

파생 개체를 사용 하려면 파생 클래스를 사용 하는 것 `CWnd` 처럼 개체의 RUNTIME_CLASS을 함수에 전달 합니다 `CreateView` `CView` . 프레임 워크에서 런타임에 동적 생성을 사용 하므로 클래스는 DECLARE_DYNCREATE 및 IMPLEMENT_DYNCREATE를 사용 해야 합니다. 에는 클래스와 관련 된 많은 코드가 있지만이 `CSplitterWnd` `CView` 작업을 수행 하기 전에는 항상 [CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) 가 사용 됩니다.

분할자 막대: 창의 행과 열 사이에 배치 되는 컨트롤입니다. 창의 행 또는 열 크기를 조정 하는 데 사용할 수 있습니다.

분할자 상자: `CSplitterWnd` 새 행 또는 창의 열을 만드는 데 사용할 수 있는 동적의 컨트롤입니다. 세로 스크롤 막대의 위쪽 또는 가로 스크롤 막대의 왼쪽에 있습니다.

분할자 교차: 세로 분할자 막대와 가로 분할자 막대의 교집합입니다. 이를 끌어서 창의 행과 열 크기를 동시에 조정할 수 있습니다.

## <a name="shared-scroll-bars"></a>공유 스크롤 막대

`CSplitterWnd`클래스는 공유 스크롤 막대도 지원 합니다. 이러한 스크롤 막대 컨트롤은의 자식이 `CSplitterWnd` 며 분할자의 여러 창과 공유 됩니다.

예를 들어 1 행 x 2 열 창에서를 만들 때 WS_VSCROLL 지정할 수 있습니다 `CSplitterWnd` . Windows에서는 두 창 사이에 공유 되는 특수 한 스크롤 막대 컨트롤을 만듭니다.

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

사용자가 스크롤 막대를 움직이면 WM_VSCROLL 메시지가 두 뷰로 모두 전송 됩니다. 두 뷰에서 모두 스크롤 막대 위치를 설정 하면 공유 스크롤 막대가 설정 됩니다.

공유 스크롤 막대는 유사한 뷰 개체에 가장 유용 합니다. 분할자에서 다양 한 형식의 뷰를 혼합 하는 경우 스크롤 위치를 조정 하는 특수 코드를 작성 해야 할 수 있습니다. `CView`스크롤 막대 api를 사용 하는 모든 파생 클래스는 `CWnd` 공유 스크롤 막대 (있는 경우)에 위임 합니다. `CScrollView`구현은 `CView` 공유 스크롤 막대를 지 원하는 클래스의 한 예입니다. 에서 파생 되지 않은 클래스 `CView` , 비 컨트롤 스크롤 막대에 의존 하는 클래스 또는 표준 Windows 구현을 사용 하는 클래스 (예:)는 `CEditView` 의 공유 스크롤 막대 기능에서 작동 하지 않습니다 `CSplitterWnd` .

## <a name="minimum-sizes"></a>최소 크기

각 행에는 최소 행 높이가 있으며 각 열에 대해 최소 열 너비가 있습니다. 이 최소값은 창이 너무 작아 전체 세부 정보에 표시 되지 않도록 보장 합니다.

정적 분할자 창의 경우 초기 최소 행 높이 및 열 너비는 0입니다. 동적 분할자 창의 경우 초기 최소 행 높이 및 열 너비는 함수의 *sizeMin* 매개 변수에 의해 설정 됩니다 `CSplitterWnd::Create` .

[CSplitterWnd:: SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) 및 [CSplitterWnd:: setcolumninfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) 함수를 사용 하 여 이러한 최소 크기를 변경할 수 있습니다.

## <a name="actual-vs-ideal-sizes"></a>실제 크기 및 이상적인 크기

분할자 창의 창 레이아웃은이를 포함 하는 프레임의 크기에 따라 달라 집니다. 사용자가 포함 하는 프레임의 크기를 조정 하면에서 `CSplitterWnd` 창의 위치를 조정 하 고 크기를 조정 하 여 가능한 한도에 맞게 창의 크기를 조정 합니다.

사용자가 행 높이 및 열 너비 크기를 수동으로 설정 하거나, 프로그램에서 클래스를 사용 하 여 이상적인 크기를 설정할 수 있습니다 `CSplitterWnd` . 실제 크기는 이상적인 크기 보다 작거나 클 수 있습니다. 이상적인 크기를 표시 하는 데 충분 한 공간이 없거나 분할자 창의 오른쪽 이나 아래쪽에 너무 많은 빈 공간이 있는 경우 Windows에서 실제 크기를 조정 합니다.

## <a name="custom-controls"></a>사용자 지정 컨트롤

여러 함수를 재정의 하 여 사용자 지정 된 동작과 사용자 지정 된 인터페이스를 제공할 수 있습니다. 이 첫 번째 집합을 재정의 하 여 분할자 창의 다양 한 그래픽 구성 요소에 대 한 대체 이미지를 제공할 수 있습니다.

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

이 함수를 호출 하 여 공유 스크롤 막대 컨트롤을 만듭니다. 이를 재정의 하 여 스크롤 막대 옆에 추가 컨트롤을 만들 수 있습니다.

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

이러한 함수는 동적 분할자 창의 논리를 구현 합니다. 이러한 재정의를 재정의 하 여 고급 분할자 논리를 제공할 수 있습니다.

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>CView 기능

`CView`클래스는 다음과 같은 높은 수준의 명령을 사용 하 여 구현에 위임 `CSplitterWnd` 합니다. 이러한 명령이 가상 이기 때문 `CView` 에 표준 구현에서는 전체 `CSplitterWnd` 구현을에 연결 하지 않아도 됩니다. 를 사용 하지만을 사용 하지 않는 응용 프로그램의 경우 `CView` `CSplitterWnd` `CSplitterWnd` 구현이 응용 프로그램과 연결 되지 않습니다.

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   ID_NEXT_PANE 또는 ID_PREV_PANE 현재 가능한 지 여부를 확인 합니다.

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   "다음 창" 또는 "이전 창" 명령을 실행 합니다.

- `virtual BOOL DoKeyboardSplit();`

   키보드 분할 명령 (일반적으로 "창 분할")을 실행 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
