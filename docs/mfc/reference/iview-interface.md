---
title: IView 인터페이스
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 9233ee5a8330c4b2c79ebc7b79e0616612c00204
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743427"
---
# <a name="iview-interface"></a>IView 인터페이스

[CWinFormsView](../../mfc/reference/cwinformsview-class.md) 에서 관리 되는 컨트롤에 뷰 알림을 보내는 데 사용 하는 여러 메서드를 구현 합니다.

## <a name="syntax"></a>구문

```
interface class IView
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[IView:: OnActivateView](#onactivateview)|뷰가 활성화 또는 비활성화 될 때 MFC에서 호출 됩니다.|
|[IView:: OnInitialUpdate](#oninitialupdate)|뷰가 문서에 처음 연결 된 후 뷰가 처음 표시 되기 전에 프레임 워크에서 호출 됩니다.|
|[IView:: OnUpdate](#onupdate)|뷰의 문서가 수정 된 후에 MFC에서 호출 됩니다. 이 함수를 사용 하면 뷰가 수정을 반영 하도록 표시를 업데이트할 수 있습니다.|

### <a name="remarks"></a>설명

`IView` 는 `CWinFormsView` 를 사용 하 여 호스트 된 관리 되는 컨트롤에 일반적인 뷰 알림을 전달 하는 여러 메서드를 구현 합니다. 이는 [Oninitialupdate](#oninitialupdate), [OnUpdate](#onupdate) 및 [oninitialupdate](#onactivateview)입니다.

`IView` 는 [CView](../../mfc/reference/cview-class.md)와 유사 하지만 관리 되는 뷰 및 컨트롤 에서만 사용 됩니다.

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

## <a name="requirements"></a>요구 사항

헤더: afxwinforms (어셈블리 atlmfc\lib\mfcmifc80.dll에 정의 됨)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a> IView:: OnActivateView

뷰가 활성화 또는 비활성화 될 때 MFC에서 호출 됩니다.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>매개 변수

*활성화*<br/>
뷰가 활성화 또는 비활성화 되는지 여부를 나타냅니다.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a> IView:: OnInitialUpdate

뷰가 문서에 처음 연결 된 후 뷰가 처음 표시 되기 전에 프레임 워크에서 호출 됩니다.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a> IView:: OnUpdate

뷰의 문서가 수정 된 후에 MFC에서 호출 됩니다.

```cpp
void OnUpdate();
```

### <a name="remarks"></a>설명

이 함수를 사용 하면 뷰가 수정을 반영 하도록 표시를 업데이트할 수 있습니다.

## <a name="see-also"></a>추가 정보

[CWinFormsView 클래스](../../mfc/reference/cwinformsview-class.md)<br/>
[CView 클래스](../../mfc/reference/cview-class.md)
