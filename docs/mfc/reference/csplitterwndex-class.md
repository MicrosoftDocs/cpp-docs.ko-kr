---
description: '자세히 알아보기: CSplitterWndEx 클래스'
title: CSplitterWndEx 클래스
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: 357f650551871cc9768c8e4e693bd62bb5e69bc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345097"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 클래스

사용자 지정된 분할자 창을 나타냅니다.

## <a name="syntax"></a>구문

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|기본 생성자입니다.|
|`CSplitterWndEx::~CSplitterWndEx`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSplitterWndEx:: OnDrawSplitter](#ondrawsplitter)|분할자 창을 그리기 위해 프레임 워크에서 호출 됩니다. [CSplitterWnd:: OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter)를 재정의 합니다.|

## <a name="remarks"></a>설명

메서드를 재정의 `OnDrawSplitter` 하 여 분할자 창의 그래픽 구성 요소 모양을 사용자 지정 합니다.

`CSplitterWndEx`클래스는 비주얼 관리자에서 구현 하는 [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)및 [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) 메서드와 함께 사용 됩니다. 시각적 관리자가 응용 프로그램에서 분할자 창을 그리도록 하려면 클래스의 선언을 `CSplitterWnd` `CSplitterWndEx` 클래스로 바꿉니다. 프레임 창 응용 프로그램의 경우 mainfrm.cpp에 있는 CMainFrame 클래스에서 분할자 창 클래스가 선언 됩니다. 예제를 보려면 `OutlookDemo` Samples 디렉터리의 샘플을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxsplitterwndex

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a> CSplitterWndEx:: OnDrawSplitter

분할자 창을 그리기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다. 이 매개 변수가 NULL 이면 프레임 워크가 활성 창을 다시 그립니다.

*nType*<br/>
진행 `CSplitterWnd::ESplitType` 그릴 분할자 창 요소를 지정 하는 열거형 값 중 하나입니다. 유효한 값은 `splitBox`, `splitBar`, `splitIntersection` 및 `splitBorder`입니다.

*rect*<br/>
진행 지정 된 분할자 창 요소를 그릴 크기와 위치를 지정 하는 경계 사각형입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../hierarchy-chart.md)<br/>
[클래스](mfc-classes.md)<br/>
[CSplitterWnd 클래스](csplitterwnd-class.md)<br/>
[CMFCVisualManager 클래스](cmfcvisualmanager-class.md)
