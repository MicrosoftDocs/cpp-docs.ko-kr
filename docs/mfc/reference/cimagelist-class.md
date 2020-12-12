---
description: '자세히 알아보기: CImageList 클래스'
title: CImageList 클래스
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: 039f4e307727970b6236af6ad51bf658c44bae0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327775"
---
# <a name="cimagelist-class"></a>CImageList 클래스

Windows의 공용 이미지 목록 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CImageList : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CImageList:: CImageList](#cimagelist)|`CImageList` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CImageList:: Add](#add)|이미지 목록에 이미지를 추가 합니다.|
|[CImageList:: Attach](#attach)|이미지 목록을 개체에 연결 `CImageList` 합니다.|
|[CImageList:: BeginDrag](#begindrag)|이미지를 끌기 시작 합니다.|
|[CImageList:: Copy](#copy)|개체 내에서 이미지를 복사 `CImageList` 합니다.|
|[CImageList:: Create](#create)|이미지 목록을 초기화 하 여 개체에 연결 `CImageList` 합니다.|
|[CImageList::D eleteImageList](#deleteimagelist)|이미지 목록을 삭제 합니다.|
|[CImageList::D eleteTempMap](#deletetempmap)|에서 만든 임시 개체를 삭제 하기 위해 [CWinApp](../../mfc/reference/cwinapp-class.md) 유휴 시간 처리기에 의해 호출 `CImageList` `FromHandle` 됩니다.|
|[CImageList::D etach](#detach)|개체에서 이미지 목록 개체를 분리 `CImageList` 하 고 이미지 목록에 대 한 핸들을 반환 합니다.|
|[CImageList::D ragEnter](#dragenter)|끌기 작업 중에 업데이트를 잠그고 지정 된 위치에 끌기 이미지를 표시 합니다.|
|[CImageList::D ragLeave](#dragleave)|창 잠금을 해제 하 고 창을 업데이트할 수 있도록 끌기 이미지를 숨깁니다.|
|[CImageList::D ragMove](#dragmove)|끌어서 놓기 작업을 수행 하는 동안 끌고 있는 이미지를 이동 합니다.|
|[CImageList::D ragShowNolock](#dragshownolock)|창을 잠그지 않고 끌기 작업 중에 끌기 이미지를 표시 하거나 숨깁니다.|
|[CImageList: 원시:D](#draw)|끌어서 놓기 작업을 수행 하는 동안 끌고 있는 이미지를 그립니다.|
|[CImageList::D rawEx](#drawex)|지정 된 장치 컨텍스트에 이미지 목록 항목을 그립니다. 함수는 지정 된 그리기 스타일을 사용 하 고 이미지를 지정 된 색으로 혼합 합니다.|
|[CImageList::D rawIndirect](#drawindirect)|이미지 목록에서 이미지를 그립니다.|
|[CImageList:: EndDrag](#enddrag)|끌기 작업을 종료 합니다.|
|[CImageList:: ExtractIcon](#extracticon)|이미지 목록의 이미지와 마스크를 기반으로 아이콘을 만듭니다.|
|[CImageList:: FromHandle](#fromhandle)|`CImageList`이미지 목록에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다. `CImageList` 개체가 핸들에 연결되지 않은 경우 임시 `CImageList` 개체를 만들어 연결합니다.|
|[CImageList:: FromHandlePermanent](#fromhandlepermanent)|`CImageList`이미지 목록에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다. `CImageList`개체가 핸들에 연결 되지 않은 경우 NULL이 반환 됩니다.|
|[CImageList:: GetBkColor](#getbkcolor)|이미지 목록의 현재 배경색을 검색 합니다.|
|[CImageList:: GetDragImage](#getdragimage)|끌기에 사용 되는 임시 이미지 목록을 가져옵니다.|
|[CImageList:: GetImageCount](#getimagecount)|이미지 목록의 이미지 수를 검색 합니다.|
|[CImageList:: GetImageInfo](#getimageinfo)|이미지에 대 한 정보를 검색합니다.|
|[CImageList:: GetSafeHandle](#getsafehandle)|`m_hImageList`를 검색 합니다.|
|[CImageList:: Read](#read)|보관 파일에서 이미지 목록을 읽습니다.|
|[CImageList:: Remove](#remove)|이미지 목록에서 이미지를 제거 합니다.|
|[CImageList:: Replace](#replace)|이미지 목록의 이미지를 새 이미지로 바꿉니다.|
|[CImageList:: SetBkColor](#setbkcolor)|이미지 목록의 배경색을 설정 합니다.|
|[CImageList:: SetDragCursorImage](#setdragcursorimage)|새 끌기 이미지를 만듭니다.|
|[CImageList:: SetImageCount](#setimagecount)|이미지 목록의 이미지 수를 다시 설정 합니다.|
|[CImageList:: SetOverlayImage](#setoverlayimage)|오버레이 마스크로 사용할 이미지 목록에 이미지의 0부터 시작 하는 인덱스를 추가 합니다.|
|[CImageList:: Write](#write)|보관에 이미지 목록을 씁니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CImageList:: operator HIMAGELIST](#operator_himagelist)|에 연결 된 HIMAGELIST를 반환 합니다 `CImageList` .|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CImageList:: m_hImageList](#m_himagelist)|이 개체에 연결 된 이미지 목록을 포함 하는 핸들입니다.|

## <a name="remarks"></a>설명

"이미지 목록"은 각각 0부터 시작 하는 인덱스에서 참조할 수 있는 동일한 크기의 이미지 컬렉션입니다. 이미지 목록은 많은 아이콘이 나 비트맵 집합을 효율적으로 관리 하는 데 사용 됩니다. 이미지 목록의 모든 이미지는 화면 장치 형식의 단일 와이드 비트맵에 포함 되어 있습니다. 이미지 목록에는 투명 하 게 이미지를 그리는 데 사용 되는 마스크를 포함 하는 단색 비트맵 (아이콘 스타일)이 포함 될 수도 있습니다. Microsoft Win32 API (응용 프로그래밍 인터페이스)는 이미지를 그리거나, 이미지 목록을 만들고 삭제 하 고, 이미지를 추가 및 제거 하 고, 이미지를 바꾸고, 이미지를 끌 수 있는 이미지 목록 함수를 제공 합니다.

이 컨트롤 (및 `CImageList` 클래스)은 windows 95/98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

사용에 대 한 자세한 내용은 `CImageList` [컨트롤](../../mfc/controls-mfc.md) 및 [CImageList 사용](../../mfc/using-cimagelist.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a> CImageList:: Add

이미지 목록에 하나 이상의 이미지 또는 아이콘을 추가 하려면이 함수를 호출 합니다.

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>매개 변수

*pbmImage*<br/>
이미지 또는 이미지를 포함 하는 비트맵에 대 한 포인터입니다. 비트맵의 너비에서 이미지 수가 유추 됩니다.

*pbmMask*<br/>
마스크를 포함 하는 비트맵에 대 한 포인터입니다. 이미지 목록과 함께 마스크가 사용 되지 않으면이 매개 변수는 무시 됩니다.

*crMask*<br/>
마스크를 생성 하는 데 사용 되는 색입니다. 지정 된 비트맵에서이 색의 각 픽셀은 검정으로 변경 되 고 마스크의 해당 비트는 1로 설정 됩니다.

*hIcon*<br/>
새 이미지에 대 한 비트맵과 마스크를 포함 하는 아이콘 핸들입니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 첫 번째 새 이미지의 인덱스 (0부터 시작)입니다. 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

작업을 완료 하면 아이콘 핸들을 해제 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a> CImageList:: Attach

이 함수를 호출 하 여 이미지 목록을 개체에 연결 `CImageList` 합니다.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>매개 변수

*hImageList*<br/>
이미지 목록 개체에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

첨부 파일이 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a> CImageList:: BeginDrag

이미지를 끌기 시작 하려면이 함수를 호출 합니다.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>매개 변수

*nImage*<br/>
끌 이미지의 인덱스 (0부터 시작)입니다.

*ptHotSpot*<br/>
시작 끌기 위치의 좌표 (일반적으로 커서 위치)입니다. 좌표는 이미지의 왼쪽 위 모퉁이를 기준으로 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 끌기에 사용 되는 임시 이미지 목록을 만듭니다. 이미지는 지정 된 이미지와 해당 마스크를 현재 커서와 결합 합니다. 후속 WM_MOUSEMOVE 메시지에 대 한 응답으로 멤버 함수를 사용 하 여 끌기 이미지를 이동할 수 있습니다 `DragMove` . 끌기 작업을 종료 하기 위해 멤버 함수를 사용할 수 있습니다 `EndDrag` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a> CImageList:: CImageList

`CImageList` 개체를 생성합니다.

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a> CImageList:: Copy

이 멤버 함수는 Windows SDK에 설명 된 대로 [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy)Win32 함수 동작을 구현 합니다.

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>매개 변수

*iDst*<br/>
복사 작업의 대상으로 사용할 이미지의 인덱스 (0부터 시작)입니다.

*iSrc*<br/>
복사 작업의 소스로 사용할 이미지의 인덱스 (0부터 시작)입니다.

*uFlags*<br/>
수행할 복사 작업의 유형을 지정 하는 비트 플래그 값입니다. 이 매개 변수는 다음 값 중 하나일 수 있습니다.

|값|의미|
|-----------|-------------|
|ILCF_MOVE|원본 이미지가 대상 이미지의 인덱스로 복사 됩니다. 이 작업을 수행 하면 지정 된 이미지의 여러 인스턴스가 생성 됩니다. 기본값은 ILCF_MOVE입니다.|
|ILCF_SWAP|원본 및 대상 이미지는 이미지 목록 내의 위치를 교환 합니다.|

*.Psrc*<br/>
`CImageList`복사 작업의 대상인 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a> CImageList:: Create

이미지 목록을 초기화 하 고 [CImageList](../../mfc/reference/cimagelist-class.md) 개체에 연결 합니다.

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>매개 변수

*cx*<br/>
각 이미지의 크기 (픽셀)입니다.

*cy*<br/>
각 이미지의 크기 (픽셀)입니다.

*nFlags*<br/>
만들 이미지 목록 유형을 지정 합니다. 이 매개 변수는 다음 값을 조합 하 여 사용할 수 있지만 값 중 하나만 포함할 수 있습니다 `ILC_COLOR` .

|값|의미|
|-----------|-------------|
|ILC_COLOR|다른 ILC_COLOR * 플래그가 지정 되지 않은 경우 기본 동작을 사용 합니다. 일반적으로 기본값은 ILC_COLOR4입니다. 그러나 이전 디스플레이 드라이버의 경우 기본값은 ILC_COLORDDB입니다.|
|ILC_COLOR4|이미지 목록에 대 한 비트맵으로 4 비트 (16 색) 장치 독립적 비트맵 (DIB) 섹션을 사용 합니다.|
|ILC_COLOR8|8 비트 DIB 섹션을 사용 합니다. 색 테이블에 사용 되는 색은 하프톤 색상표와 동일한 색입니다.|
|ILC_COLOR16|16 비트 (32/64k 색) DIB 섹션을 사용 합니다.|
|ILC_COLOR24|24 비트 DIB 섹션을 사용 합니다.|
|ILC_COLOR32|32 비트 DIB 섹션을 사용 합니다.|
|ILC_COLORDDB|장치 종속 비트맵을 사용 합니다.|
|ILC_MASK|마스크를 사용 합니다. 이미지 목록에는 두 개의 비트맵이 포함 되며,이 중 하나는 마스크로 사용 되는 단색 비트맵입니다. 이 값이 포함 되지 않은 경우에는 이미지 목록에 하나의 비트맵만 포함 됩니다. 마스킹된 이미지에 대 한 추가 정보는 [이미지 목록에서 이미지 그리기](../../mfc/drawing-images-from-an-image-list.md) 를 참조 하세요.|

*nInitial*<br/>
이미지 목록에 처음 포함 된 이미지 수입니다.

*n 증가*<br/>
새 이미지를 위한 공간을 만들기 위해 시스템에서 목록의 크기를 조정 해야 하는 경우 이미지 목록이 증가할 수 있는 이미지 수입니다. 이 매개 변수는 크기 조정 된 이미지 목록에 포함할 수 있는 새 이미지 수를 나타냅니다.

*nBitmapID*<br/>
이미지 목록과 연결할 비트맵의 리소스 Id입니다.

*crMask*<br/>
마스크를 생성 하는 데 사용 되는 색입니다. 지정 된 비트맵에서이 색의 각 픽셀은 검정으로 변경 되 고 마스크의 해당 비트는 1로 설정 됩니다.

*lpszBitmapID*<br/>
이미지의 리소스 Id를 포함 하는 문자열입니다.

*imagelist1*<br/>
`CImageList` 개체에 대한 참조입니다.

*nImage1*<br/>
첫 번째 기존 이미지의 인덱스입니다.

*imagelist2*<br/>
`CImageList` 개체에 대한 참조입니다.

*nImage2*<br/>
두 번째 기존 이미지의 인덱스입니다.

*dx*<br/>
첫 번째 이미지와 관계 된 두 번째 이미지의 x 축 오프셋 (픽셀)입니다.

*dy*<br/>
첫 번째 이미지와 관계 된 두 번째 이미지의 y 축 오프셋 (픽셀)입니다.

*pImageList*<br/>
`CImageList` 개체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CImageList`두 단계로을 생성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` 이미지 목록을 만들고이를 개체에 연결 `CImageList` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a> CImageList::D eleteImageList

이미지 목록을 삭제 하려면이 함수를 호출 합니다.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a> CImageList::D eleteTempMap

유휴 시간 처리기에서 자동으로 호출 `CWinApp` 되며, `DeleteTempMap` `CImageList` [fromhandle](#fromhandle)에 의해 생성 된 모든 임시 개체를 삭제 하지만 `hImageList` 개체와 일시적으로 연결 된 핸들 ()은 소멸 하지 않습니다 `ImageList` .

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a> CImageList::D etach

개체에서 이미지 목록 개체를 분리 하려면이 함수를 호출 `CImageList` 합니다.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>반환 값

이미지 목록 개체에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 함수는 이미지 목록 개체에 대 한 핸들을 반환 합니다.

### <a name="example"></a>예제

  [CImageList:: Attach](#attach)의 예제를 참조 하세요.

## <a name="cimagelistdragenter"></a><a name="dragenter"></a> CImageList::D ragEnter

끌기 작업 중에는 *pWndLock* 로 지정 된 창으로 업데이트를 잠그고 *point* 로 지정 된 위치에 끌기 이미지를 표시 합니다.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>매개 변수

*pWndLock*<br/>
끌기 이미지를 소유 하는 창에 대 한 포인터입니다.

*까지*<br/>
끌기 이미지를 표시할 위치입니다. 좌표는 창의 왼쪽 위 모퉁이를 기준으로 합니다 (클라이언트 영역이 아님).

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

좌표는 창의 왼쪽 위 모퉁이를 기준으로 하므로 좌표를 지정할 때 테두리, 제목 표시줄 및 메뉴 모음 등의 창 요소 너비를 보정 해야 합니다.

*PWndLock* 가 NULL 인 경우이 함수는 바탕 화면 창과 연결 된 표시 컨텍스트에 이미지를 그리고 좌표는 화면의 왼쪽 위 모퉁이를 기준으로 합니다.

이 함수는 끌기 작업을 수행 하는 동안 지정 된 창에 대 한 다른 모든 업데이트를 잠급니다. 끌기 작업을 수행 하는 동안 그리기를 수행 해야 하는 경우 (예: 끌어서 놓기 작업의 대상 강조 표시) [CImageList::D ragleave](#dragleave) 함수를 사용 하 여 끌어 온 이미지를 일시적으로 숨길 수 있습니다.

### <a name="example"></a>예제

  [CImageList:: BeginDrag](#begindrag)의 예제를 참조 하세요.

## <a name="cimagelistdragleave"></a><a name="dragleave"></a> CImageList::D ragLeave

*PWndLock* 에 지정 된 창의 잠금을 해제 하 고 끌기 이미지를 숨겨 창이 업데이트 될 수 있도록 합니다.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>매개 변수

*pWndLock*<br/>
끌기 이미지를 소유 하는 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CImageList:: EndDrag](#enddrag)의 예제를 참조 하세요.

## <a name="cimagelistdragmove"></a><a name="dragmove"></a> CImageList::D ragMove

끌어서 놓기 작업을 수행 하는 동안 끌고 있는 이미지를 이동 하려면이 함수를 호출 합니다.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
새 끌기 위치입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 WM_MOUSEMOVE 메시지에 대 한 응답으로 호출 됩니다. 끌기 작업을 시작 하려면 `BeginDrag` 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a> CImageList::D ragShowNolock

창을 잠그지 않고 끌기 작업 중에 끌기 이미지를 표시 하거나 숨깁니다.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
끌기 이미지를 표시할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[CImageList::D ragenter](#dragenter) 함수는 끌기 작업 중에 창에 대 한 모든 업데이트를 잠급니다. 그러나이 함수는 창을 잠그지 않습니다.

## <a name="cimagelistdraw"></a><a name="draw"></a> CImageList: 원시:D

끌어서 놓기 작업을 수행 하는 동안 끌고 있는 이미지를 그리려면이 함수를 호출 합니다.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
대상 장치 컨텍스트에 대 한 포인터입니다.

*nImage*<br/>
그릴 이미지의 0부터 시작 하는 인덱스입니다.

*pt*<br/>
지정 된 장치 컨텍스트 내에서 그릴 위치입니다.

*nStyle*<br/>
그리기 스타일을 지정 하는 플래그입니다. 다음 값 중 하나 이상이 될 수 있습니다.

|값|의미|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|시스템 강조 색을 사용 하 여 25% 혼합 된 이미지를 그립니다. 이미지 목록에 마스크가 포함 되지 않은 경우에는이 값이 적용 되지 않습니다.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|시스템 강조 색으로 50%를 혼합 하 여 이미지를 그립니다. 이미지 목록에 마스크가 포함 되지 않은 경우에는이 값이 적용 되지 않습니다.|
|ILD_MASK|마스크를 그립니다.|
|ILD_NORMAL|이미지 목록의 배경색을 사용 하 여 이미지를 그립니다. 배경색이 CLR_NONE 값 이면 마스크를 사용 하 여 이미지가 투명 하 게 그려집니다.|
|ILD_TRANSPARENT|배경 색에 관계 없이 마스크를 사용 하 여 투명 하 게 이미지를 그립니다.|

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CImageList:: SetOverlayImage](#setoverlayimage)의 예제를 참조 하세요.

## <a name="cimagelistdrawex"></a><a name="drawex"></a> CImageList::D rawEx

지정 된 장치 컨텍스트에 이미지 목록 항목을 그립니다.

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
대상 장치 컨텍스트에 대 한 포인터입니다.

*nImage*<br/>
그릴 이미지의 0부터 시작 하는 인덱스입니다.

*pt*<br/>
지정 된 장치 컨텍스트 내에서 그릴 위치입니다.

*sz*<br/>
이미지의 왼쪽 위 모퉁이를 기준으로 그릴 이미지 부분의 크기입니다. Windows SDK에서 [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) *dx* 및 *dy* 를 참조 하세요.

*clrBk*<br/>
이미지의 배경색입니다. Windows SDK에서 [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) *rgbBk* 를 참조 하세요.

*clrFg*<br/>
이미지의 전경색입니다. Windows SDK에서 [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) *rgbFg* 를 참조 하세요.

*nStyle*<br/>
그리기 스타일을 지정 하는 플래그입니다. Windows SDK에서 [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) 의 *fstyle* 을 참조 하십시오.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

함수는 지정 된 그리기 스타일을 사용 하 고 이미지를 지정 된 색으로 혼합 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a> CImageList::D rawIndirect

이미지 목록에서 이미지를 그리려면이 멤버 함수를 호출 합니다.

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>매개 변수

*pimldp*<br/>
그리기 작업에 대 한 정보가 포함 된 [Imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) 구조체에 대 한 포인터입니다.

*컨트롤러가*<br/>
대상 장치 컨텍스트에 대 한 포인터입니다. 작업을 완료 한 후에는이 [CDC](../../mfc/reference/cdc-class.md) 개체를 삭제 해야 합니다.

*nImage*<br/>
그릴 이미지의 인덱스 (0부터 시작)입니다.

*pt*<br/>
이미지를 그릴 x 및 y 좌표를 포함 하는 [점](/windows/win32/api/windef/ns-windef-point) 구조입니다.

*sz*<br/>
그릴 이미지의 크기를 나타내는 [크기](/windows/win32/api/windef/ns-windef-size) 구조체입니다.

*ptOrigin*<br/>
이미지 자체를 기준으로 그리기 작업의 왼쪽 위 모퉁이를 지정 하는 x 및 y 좌표를 포함 하는 [점](/windows/win32/api/windef/ns-windef-point) 구조입니다. X 좌표와 y 좌표 위에 있는 이미지의 픽셀은 그려지지 않습니다.

*fStyle*<br/>
그리기 스타일 및 필요한 경우 오버레이 이미지를 지정 하는 플래그입니다. 오버레이 이미지에 대 한 자세한 내용은 설명 섹션을 참조 하세요. MFC 기본 구현인 ILD_NORMAL는 이미지 목록의 배경색을 사용 하 여 이미지를 그립니다. 배경색이 CLR_NONE 값 이면 마스크를 사용 하 여 이미지가 투명 하 게 그려집니다.

다른 가능한 스타일은 [Imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) 구조체의 *fstyle* 멤버 아래에 설명 되어 있습니다.

*dwRop*<br/>
래스터 작업 코드를 지정 하는 값입니다. 이러한 코드는 최종 색을 얻기 위해 소스 사각형의 색 데이터를 대상 사각형의 색 데이터와 결합 하는 방법을 정의 합니다. MFC의 기본 구현인 SRCCOPY는 소스 사각형을 대상 사각형에 직접 복사 합니다. *Fstyle* 매개 변수에 ILD_ROP 플래그가 포함 되어 있지 않으면이 매개 변수는 무시 됩니다.

다른 가능한 값은 [Imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) 구조체의 *dwRop* 멤버 아래에 설명 되어 있습니다.

*rgbBack*<br/>
기본적으로 CLR_DEFAULT 이미지 배경색입니다. 이 매개 변수는 응용 프로그램 정의 RGB 값 이거나 다음 값 중 하나일 수 있습니다.

|값|의미|
|-----------|-------------|
|CLR_DEFAULT|기본 배경색입니다. 이미지 목록 배경색을 사용 하 여 이미지를 그립니다.|
|CLR_NONE|배경 색이 없습니다. 이미지가 투명 하 게 그려집니다.|

*rgbFore*<br/>
기본적으로 CLR_DEFAULT 이미지 전경색입니다. 이 매개 변수는 응용 프로그램 정의 RGB 값 이거나 다음 값 중 하나일 수 있습니다.

|값|의미|
|-----------|-------------|
|CLR_DEFAULT|기본 전경색입니다. 시스템 강조 색을 전경색으로 사용 하 여 이미지를 그립니다.|
|CLR_NONE|혼합 색이 없습니다. 이미지가 대상 장치 컨텍스트의 색과 혼합 되어 있습니다.|

이 매개 변수는 *Fstyle* 에 ILD_BLEND25 또는 ILD_BLEND50 플래그가 포함 된 경우에만 사용 됩니다.

*fState*<br/>
그리기 상태를 지정 하는 플래그입니다. 이 멤버는 하나 이상의 이미지 목록 상태 플래그를 포함할 수 있습니다.

*Frame*<br/>
는 포화 및 알파 혼합 효과의 동작에 영향을 줍니다.

ILS_SATURATE와 함께 사용 하는 경우이 멤버는 아이콘의 각 픽셀에 대해 RGB의 각 색 구성 요소에 추가 되는 값을 보유 합니다.

ILS_APLHA와 함께 사용 하는 경우이 멤버는 알파 채널에 대 한 값을 보유 합니다. 이 값은 0부터 255 까지입니다. 0은 완전히 투명 하 고 255은 완전히 불투명 합니다.

*crEffect*<br/>
네온 및 그림자 효과에 사용 되는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="return-value"></a>반환 값

이미지가 성공적으로 그려진 경우 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

Win32 구조를 직접 입력 하려면 첫 번째 버전을 사용 합니다. 하나 이상의 MFC 기본 인수를 활용 하거나 구조를 관리 하지 않으려는 경우 두 번째 버전을 사용 합니다.

오버레이 이미지는이 멤버 함수에서 *Nimage* 매개 변수로 지정 하는 기본 이미지의 맨 위에 그려지는 이미지입니다. [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) 매크로를 사용 하 여 지정한 오버레이 마스크의 1부터 시작 하는 인덱스와 함께 [draw](#draw) 멤버 함수를 사용 하 여 오버레이 마스크를 그립니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a> CImageList:: EndDrag

이 함수를 호출 하 여 끌기 작업을 종료 합니다.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>설명

끌기 작업을 시작 하려면 `BeginDrag` 멤버 함수를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a> CImageList:: ExtractIcon

이미지 목록에서 이미지 및 관련 마스크에 따라 아이콘을 만들려면이 함수를 호출 합니다.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>매개 변수

*nImage*<br/>
이미지의 0부터 시작 하는 인덱스입니다.

### <a name="return-value"></a>반환 값

성공 하면 아이콘 핸들 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) 매크로의 동작에 의존 하 여 아이콘을 만듭니다. 아이콘 만들기 및 정리에 대 한 자세한 내용은 [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) 매크로를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a> CImageList:: FromHandle

`CImageList`이미지 목록에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>매개 변수

*hImageList*<br/>
이미지 목록을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 개체에 대 한 포인터 `CImageList` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`CImageList`가 핸들에 아직 연결 되지 않은 경우 임시 `CImageList` 개체가 만들어지고 연결 됩니다. 이 임시 `CImageList` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과 하 여 모든 임시 개체가 삭제 될 때 까지만 유효 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a> CImageList:: FromHandlePermanent

`CImageList`이미지 목록에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>매개 변수

*hImageList*<br/>
이미지 목록을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 개체에 대 한 포인터 `CImageList` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`CImageList`개체가 핸들에 연결 되지 않은 경우 NULL이 반환 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a> CImageList:: GetBkColor

이미지 목록의 현재 배경색을 검색 하려면이 함수를 호출 합니다.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>반환 값

개체 배경색의 RGB 색 값입니다 `CImageList` .

### <a name="example"></a>예제

  [CImageList:: SetBkColor](#setbkcolor)의 예제를 참조 하세요.

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a> CImageList:: GetDragImage

끌기에 사용 되는 임시 이미지 목록을 가져옵니다.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>매개 변수

*lpPoint*<br/>
현재 끌기 위치를 받는 [점](/windows/win32/api/windef/ns-windef-point) 구조의 주소입니다.

*lpPointHotSpot*<br/>
끌기 `POINT` 위치를 기준으로 하는 끌기 이미지의 오프셋을 받는 구조체의 주소입니다.

### <a name="return-value"></a>반환 값

성공 하면 끌기에 사용 되는 임시 이미지 목록에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a> CImageList:: GetImageCount

이미지 목록의 이미지 수를 검색 하려면이 함수를 호출 합니다.

```
int GetImageCount() const;
```

### <a name="return-value"></a>반환 값

이미지 수입니다.

### <a name="example"></a>예제

  [CImageList:: ExtractIcon](#extracticon)의 예제를 참조 하세요.

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a> CImageList:: GetImageInfo

이미지에 대 한 정보를 검색 하려면이 함수를 호출 합니다.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>매개 변수

*nImage*<br/>
이미지의 0부터 시작 하는 인덱스입니다.

*pImageInfo*<br/>
이미지에 대 한 정보를 받는 [Imageinfo](/windows/win32/api/commctrl/ns-commctrl-imageinfo) 구조체에 대 한 포인터입니다. 이 구조체의 정보는 이미지에 대 한 비트맵을 직접 조작 하는 데 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`IMAGEINFO`구조는 이미지 목록의 이미지에 대 한 정보를 포함 합니다.

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a> CImageList:: GetSafeHandle

데이터 멤버를 검색 하려면이 함수를 호출 `m_hImageList` 합니다.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>반환 값

연결 된 이미지 목록에 대 한 핸들입니다. 개체가 연결 되어 있지 않으면 NULL입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a> CImageList:: m_hImageList

이 개체에 연결 된 이미지 목록의 핸들입니다.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>설명

`m_hImageList`데이터 멤버는 HIMAGELIST 형식의 공용 변수입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a> CImageList:: operator HIMAGELIST

이 연산자를 사용 하 여 개체의 연결 된 핸들을 가져옵니다 `CImageList` .

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>반환 값

성공 하면 개체가 나타내는 이미지 목록에 대 한 핸들이 고, `CImageList` 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 연산자는 HIMAGELIST 개체의 직접 사용을 지 원하는 캐스팅 연산자입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a> CImageList:: Read

이 함수를 호출 하 여 보관 파일에서 이미지 목록을 읽습니다.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>매개 변수

*pArchive*<br/>
`CArchive`이미지 목록을 읽을 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a> CImageList:: Remove

이미지 목록 개체에서 이미지를 제거 하려면이 함수를 호출 합니다.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>매개 변수

*nImage*<br/>
제거할 이미지의 0부터 시작 하는 인덱스입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Nimage* 뒤에 나오는 모든 항목은 이제 한 위치 아래로 이동 합니다. 예를 들어 이미지 목록에 두 개의 항목이 포함 된 경우 첫 번째 항목을 삭제 하면 나머지 항목이 현재 첫 번째 위치에 있게 됩니다. *n 이미지*= 0은 첫 번째 위치의 항목입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a> CImageList:: Replace

이미지 목록의 이미지를 새 이미지로 바꾸려면이 함수를 호출 합니다.

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>매개 변수

*nImage*<br/>
바꿀 이미지의 인덱스 (0부터 시작)입니다.

*pbmImage*<br/>
이미지를 포함 하는 비트맵에 대 한 포인터입니다.

*pbmMask*<br/>
마스크를 포함 하는 비트맵에 대 한 포인터입니다. 이미지 목록과 함께 마스크가 사용 되지 않으면이 매개 변수는 무시 됩니다.

*hIcon*<br/>
새 이미지에 대 한 비트맵과 마스크를 포함 하는 아이콘에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

성공 하면 BOOL을 반환 하는 버전은 0이 아닌 값을 반환 합니다. 그렇지 않으면 0입니다.

성공 하면 버전 반환에서 **`int`** 이미지의 0부터 시작 하는 인덱스이 고, 그렇지 않으면-1입니다.

### <a name="remarks"></a>설명

[SetImageCount](#setimagecount) 를 호출한 후이 멤버 함수를 호출 하 여 새 유효한 이미지를 자리 표시자 이미지 인덱스 번호에 할당 합니다.

### <a name="example"></a>예제

  [CImageList:: SetImageCount](#setimagecount)의 예제를 참조 하세요.

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a> CImageList:: SetBkColor

이미지 목록의 배경색을 설정 하려면이 함수를 호출 합니다.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>매개 변수

*cr*<br/>
설정할 배경색입니다. CLR_NONE 수 있습니다. 이 경우 이미지는 마스크를 사용 하 여 투명 하 게 그려집니다.

### <a name="return-value"></a>반환 값

성공 하면 이전 배경색입니다. 그렇지 않으면 CLR_NONE 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a> CImageList:: SetDragCursorImage

지정 된 이미지 (일반적으로 마우스 커서 이미지)와 현재 끌기 이미지를 결합 하 여 새 끌기 이미지를 만듭니다.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>매개 변수

*nDrag*<br/>
끌기 이미지와 결합할 새 이미지의 인덱스입니다.

*ptHotSpot*<br/>
새 이미지 내 핫 스폿의 위치입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

끌기 작업을 수행 하는 동안 끌기 함수는 새 이미지를 사용 하기 때문에를 호출한 후에는 Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) 함수를 사용 하 여 실제 마우스 커서를 숨겨야 합니다 `CImageList::SetDragCursorImage` . 그렇지 않으면 끌기 작업 기간 동안 두 개의 마우스 커서가 있는 시스템에 표시 될 수 있습니다.

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a> CImageList:: SetImageCount

개체의 이미지 수를 다시 설정 하려면이 멤버 함수를 호출 `CImageList` 합니다.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>매개 변수

*uNewCount*<br/>
이미지 목록의 새 총 이미지 수를 지정 하는 값입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 호출 하 여 이미지 목록의 이미지 수를 늘린 경우 각 추가 이미지에 대해 [Replace](#replace) 를 호출 하 여 새 인덱스를 올바른 이미지에 할당 합니다. 인덱스를 올바른 이미지에 할당 하지 못한 경우 새 이미지를 만드는 그리기 작업을 예측할 수 없습니다.

이 함수를 사용 하 여 이미지 목록의 크기를 줄이면 잘린 이미지가 해제 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a> CImageList:: SetOverlayImage

오버레이 마스크로 사용할 이미지 목록에 이미지의 0부터 시작 하는 인덱스를 추가 하려면이 함수를 호출 합니다.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>매개 변수

*nImage*<br/>
오버레이 마스크로 사용할 이미지의 0부터 시작 하는 인덱스입니다.

*nOverlay*<br/>
오버레이 마스크의 인덱스 (1부터 사용)입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

최대 4 개의 인덱스를 목록에 추가할 수 있습니다.

오버레이 마스크는 다른 이미지 위에 투명 하 게 그려진 이미지입니다. INDEXTOOVERLAYMASK 매크로를 사용 하 여 지정한 오버레이 마스크의 인덱스 (1부터 시작)를 사용 하 여 [CImageList::D raw](#draw) 멤버 함수를 사용 하 여 이미지에 오버레이 마스크를 그립니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a> CImageList:: Write

보관에 이미지 목록 개체를 쓰려면이 함수를 호출 합니다.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>매개 변수

*pArchive*<br/>
이미지 목록이 저장 되는 개체에 대 한 포인터입니다 `CArchive` .

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl 클래스](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl 클래스](../../mfc/reference/ctabctrl-class.md)
