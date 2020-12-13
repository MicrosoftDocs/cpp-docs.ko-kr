---
description: '자세히 알아보기: CMFCSpinButtonCtrl 클래스'
title: CMFCSpinButtonCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 87e9abc94247416704ab801beeaa1953c4cceb46
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339639"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl 클래스

`CMFCSpinButtonCtrl`클래스는 spin button 컨트롤을 그리는 비주얼 관리자를 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|기본 생성자입니다.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCSpinButtonCtrl:: OnDraw](#ondraw)|현재 spin button 컨트롤을 다시 그립니다.|

## <a name="remarks"></a>설명

비주얼 관리자를 사용 하 여 응용 프로그램에서 spin button 컨트롤을 그리려면 클래스의 모든 인스턴스를 `CSpinButtonCtrl` `CMFCSpinButtonCtrl` 클래스로 바꿉니다.

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 만들고 해당 메서드를 사용 하는 방법을 보여 줍니다 `CMFCSpinButtonCtrl` `Create` .

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxspinbuttonctrl

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a> CMFCSpinButtonCtrl:: OnDraw

현재 spin button 컨트롤을 다시 그립니다.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

프레임 워크는 메서드를 호출 `CMFCSpinButtonCtrl::OnPaint` 하 여 [CWnd:: OnPaint](../../mfc/reference/cwnd-class.md#onpaint) 메시지를 처리 하 고이 메서드는이 `CMFCSpinButtonCtrl::OnDraw` 메서드를 호출 합니다. 프레임 워크가 spin button 컨트롤을 그리는 방식을 사용자 지정 하려면이 메서드를 재정의 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 클래스](../../mfc/reference/cmfcvisualmanager-class.md)
