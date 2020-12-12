---
description: '자세히 알아보기: CMFCDisableMenuAnimation 클래스'
title: CMFCDisableMenuAnimation 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: fc869570865d8b99d29e0248afeeb133e657a908
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250701"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 클래스

팝업 메뉴 애니메이션을 사용 하지 않도록 설정 합니다.

## <a name="syntax"></a>구문

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|`CMFCDisableMenuAnimation` 개체를 생성합니다.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCDisableMenuAnimation:: Restore](#restore)|프레임 워크에서 팝업 메뉴를 표시 하는 데 사용 하는 이전 애니메이션을 복원 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|`CMFCDisableMenuAnimation::m_animType`|이전 팝업 메뉴 애니메이션 유형을 저장 합니다.|

### <a name="remarks"></a>설명

이 도우미 클래스를 사용 하 여 팝업 메뉴 애니메이션 (예: 마우스 또는 키보드 명령을 처리할 때)을 일시적으로 사용 하지 않도록 설정할 수 있습니다.

`CMFCDisableMenuAnimation`개체는 수명 동안 팝업 메뉴 애니메이션을 사용 하지 않도록 설정 합니다. 생성자는 현재 팝업 메뉴 애니메이션 형식을 필드에 저장 하 `m_animType` 고 현재 애니메이션 형식을로 설정 합니다 `CMFCPopupMenu::NO_ANIMATION` . 소멸자는 이전 애니메이션 유형을 복원 합니다.

스택에 개체를 만들어 `CMFCDisableMenuAnimation` 단일 함수 전체에서 팝업 메뉴 애니메이션을 사용 하지 않도록 설정할 수 있습니다. 함수 간에 팝업 메뉴 애니메이션을 사용 하지 않도록 설정 하려면 `CMFCDisableMenuAnimation` 힙에서 개체를 만든 다음 팝업 메뉴 애니메이션을 복원 하려는 경우 삭제 합니다.

## <a name="example"></a>예제

다음 예제에서는 스택을 사용 하 여 메뉴 애니메이션을 일시적으로 해제 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpopupmenu

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a> CMFCDisableMenuAnimation:: Restore

프레임 워크에서 팝업 메뉴를 표시 하는 데 사용 하는 이전 애니메이션을 복원 합니다.

```cpp
void Restore ();
```

### <a name="remarks"></a>설명

이 메서드는 `CMFCDisableMenuAnimation` 프레임 워크에서 팝업 메뉴를 표시 하는 데 사용 된 이전 애니메이션을 복원 하기 위해 소멸자에서 호출 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 클래스](../../mfc/reference/cmfcpopupmenu-class.md)
