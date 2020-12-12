---
description: '자세한 정보: Cmfc리본 구분 기호 클래스'
title: Cmfc리본 구분 기호 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: db8e7f92089d1e6332fdb2ad057398c465c72f97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321750"
---
# <a name="cmfcribbonseparator-class"></a>Cmfc리본 구분 기호 클래스

리본 구분 기호를 구현 합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|[Cmfc리본 구분 기호:: Cmfc리본 구분 기호](#cmfcribbonseparator)|`CMFCRibbonSeparator` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[Cmfc리본 구분 기호:: AddToListBox](#addtolistbox)|**사용자 지정** 대화 상자의 **명령** 목록에 구분 기호를 추가 합니다. [Cmfc리본 Baseelement:: AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)를 재정의 합니다.|
|`CMFCRibbonSeparator::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCRibbonSeparator::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|-|-|
|[Cmfc리본 구분 기호:: CopyFrom](#copyfrom)|다른 개체에서 구분 기호의 멤버 변수를 설정 하는 복사 메서드입니다.|
|[Cmfc리본 구분 기호:: GetRegularSize](#getregularsize)|구분 기호의 크기를 반환 합니다.|
|[Cmfc리본 구분 기호:: IsSeparator](#isseparator)|구분 기호 인지 여부를 나타냅니다.|
|[Cmfc리본 구분 기호:: IsTabStop](#istabstop)|탭 정지 인지 여부를 나타냅니다.|
|[Cmfc리본 구분 기호:: OnDraw](#ondraw)|리본 또는 빠른 실행 도구 모음에 구분 기호를 그리기 위해 시스템에 의해 호출 됩니다.|
|[Cmfc리본 구분 기호:: OnDrawOnList](#ondrawonlist)|**명령** 목록에 구분 기호를 그리기 위해 시스템에 의해 호출 됩니다.|

## <a name="remarks"></a>설명

리본 구분 기호는 리본 요소를 논리적으로 구분 하는 세로 또는 가로 선입니다. 리본 컨트롤, 주 응용 프로그램 메뉴, 리본 상태 표시줄 및 빠른 실행 도구 모음에 구분 기호를 그릴 수 있습니다.

응용 프로그램에서 구분 기호를 사용 하려면 다음과 같이 새 개체를 생성 하 고 주 응용 프로그램 메뉴에 추가 합니다.

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

[Cmfc리본 패널:: AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) 를 호출 하 여 리본 패널에 구분 기호를 추가 합니다. 구분 기호는 메서드에 의해 내부적으로 할당 되 고 추가 됩니다 `AddSeparator` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[Cmfc리본 구분 기호](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a> Cmfc리본 구분 기호:: AddToListBox

**사용자 지정** 대화 상자의 **명령** 목록에 구분 기호를 추가 합니다.

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>매개 변수

*pWndListBox*<br/>
진행 구분 기호가 추가 된 **명령** 목록에 대 한 포인터입니다.

*bDeep*<br/>
진행 무시.

### <a name="return-value"></a>반환 값

*PWndListBox* 에 의해 지정 된 목록 상자의 문자열에 대 한 0부터 시작 하는 인덱스입니다.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a> Cmfc리본 구분 기호:: Cmfc리본 구분 기호

`CMFCRibbonSeparator` 개체를 생성합니다.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>매개 변수

*bIsHoriz*<br/>
진행 TRUE 이면 구분 기호가 가로 방향입니다. FALSE 이면 구분 기호가 세로 방향입니다.

### <a name="remarks"></a>설명

가로 구분 기호는 응용 프로그램 메뉴에 사용 됩니다. 세로 구분 기호는 도구 모음에 사용 됩니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하는 방법을 보여 줍니다 `CMFCRibbonSeparator` .

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a> Cmfc리본 구분 기호:: CopyFrom

다른 개체에서 구분 기호의 멤버 변수를 설정 하는 복사 메서드입니다.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>매개 변수

*소스*<br/>
진행 복사할 원본 리본 요소입니다.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a> Cmfc리본 구분 기호:: GetRegularSize

구분 기호의 크기를 반환 합니다.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 콘텐츠에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 장치 컨텍스트에서 구분 기호의 크기입니다.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a> Cmfc리본 구분 기호:: IsSeparator

구분 기호 인지 여부를 나타냅니다.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>반환 값

이 클래스의 경우 항상 TRUE입니다.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a> Cmfc리본 구분 기호:: IsTabStop

탭 정지 인지 여부를 나타냅니다.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>반환 값

이 클래스의 경우 항상 FALSE입니다.

### <a name="remarks"></a>설명

리본 구분 기호가 탭 중지가 아닙니다.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a> Cmfc리본 구분 기호:: OnDraw

리본 또는 빠른 실행 도구 모음에 구분 기호를 그리기 위해 시스템에 의해 호출 됩니다.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a> Cmfc리본 구분 기호:: OnDrawOnList

**명령** 목록에 구분 기호를 그리기 위해 시스템에 의해 호출 됩니다.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*\
진행 장치 컨텍스트에 대 한 포인터입니다.

*strText*\
진행 목록에 표시 되는 텍스트입니다.

*nTextOffset*\
진행 경계 사각형의 왼쪽 텍스트와 왼쪽 사이의 간격입니다.

*직교*\
진행 경계 사각형을 지정 합니다.

*bIsSelected*\
진행 무시.

*bHighlighted 표시*\
진행 무시.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)
