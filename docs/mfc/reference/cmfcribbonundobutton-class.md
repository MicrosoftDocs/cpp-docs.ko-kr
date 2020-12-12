---
description: '자세한 정보: Cmfc리본을 추가 하는 단추 클래스'
title: Cmfc리본를 위한 단추 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: 8bfc02b61160a5f11a6913736c5dc784c4d00ce4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264936"
---
# <a name="cmfcribbonundobutton-class"></a>Cmfc리본를 위한 단추 클래스

`CMFCRibbonUndoButton`클래스는 가장 최근의 사용자 명령이 포함 된 드롭다운 목록 단추를 구현 합니다. 사용자는 드롭다운 목록에서 가장 최근 명령 중 하나 이상을 선택 하 여 다시 실행 하거나 실행 취소할 수 있습니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfc리본를 수행 하는 단추:: Cmfc리본를 수행 하는 단추](#cmfcribbonundobutton)|`CMFCRibbonUndoButton`지정한 명령 ID, 부모 개체의 이미지 목록에서 텍스트 레이블 및 이미지를 사용 하 여 새 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 해결 단추:: Add작업](#addundoaction)|작업 목록에 새 작업을 추가 합니다.|
|[Cmfc리본 CleanUpUndoList 단추::](#cleanupundolist)|드롭다운 목록 인 작업 목록을 지웁니다.|
|[Cmfc리본를 수행 하는 단추:: GetActionNumber](#getactionnumber)|드롭다운 목록에서 사용자가 선택한 항목의 수를 결정 합니다.|
|[Cmfc리본를 수행 하는 단추:: HasMenu](#hasmenu)|개체에 메뉴가 포함 되는지 여부를 나타냅니다.|

## <a name="remarks"></a>설명

`CMFCRibbonUndoButton`클래스는 스택을 사용 하 여 드롭다운 목록을 나타냅니다.

## <a name="example"></a>예제

다음 예제에서는 클래스의 개체를 생성 하 `CMFCRibbonUndoButton` 고 동작 목록에 새 작업을 추가 하는 방법을 보여 줍니다. 이 코드 조각은 [리본 가젯 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonundobutton

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a> Cmfc리본 해결 단추:: Add작업

작업 목록에 새 작업을 추가 합니다.

```cpp
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>매개 변수

*lpszLabel*<br/>
진행 드롭다운 목록에 표시 되는 작업 레이블입니다.

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a> Cmfc리본 CleanUpUndoList 단추::

드롭다운 목록 인 작업 목록을 지웁니다.

```cpp
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a> Cmfc리본를 수행 하는 단추:: Cmfc리본를 수행 하는 단추

`CMFCRibbonUndoButton`지정한 명령 ID, 부모 개체의 이미지 목록에서 텍스트 레이블 및 이미지를 사용 하 여 새 개체를 생성 합니다.

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 명령 식별자를 지정 합니다.

*lpszText*<br/>
진행 단추의 텍스트 레이블을 지정 합니다.

*nSmallImageIndex*<br/>
진행 단추의 작은 이미지에 대 한 부모 개체의 이미지 목록에서 인덱스 (0부터 시작)입니다.

*nLargeImageIndex*<br/>
진행 단추의 초대형 이미지에 대 한 부모 개체의 이미지 목록에 있는 인덱스 (0부터 시작)입니다.

*hIcon*<br/>
진행 단추의 이미지로 사용할 수 있는 아이콘에 대 한 핸들입니다.

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a> Cmfc리본를 수행 하는 단추:: GetActionNumber

드롭다운 목록에서 사용자가 선택한 항목의 수를 결정 합니다.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>반환 값

사용자가 선택한 항목 수입니다.

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a> Cmfc리본를 수행 하는 단추:: HasMenu

개체에 메뉴가 포함 되는지 여부를 나타냅니다.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>반환 값

항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 갤러리 클래스](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[Cmfc리본 단추 클래스](../../mfc/reference/cmfcribbonbutton-class.md)
