---
description: '다음에 대 한 자세한 정보: CKeyFrame 클래스'
title: CKeyFrame 클래스
ms.date: 11/04/2016
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
ms.openlocfilehash: ec6aa45484965afbf0c636a1eed26a3d4a63e426
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236882"
---
# <a name="ckeyframe-class"></a>CKeyFrame 클래스

애니메이션 키프레임을 나타냅니다.

## <a name="syntax"></a>구문

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CKeyFrame:: CKeyFrame](#ckeyframe)|오버로드됨. 다른 키프레임에 종속 되는 키 프레임을 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CKeyFrame::가 중 Storyboard](#addtostoryboard)|Storyboard에 키 프레임을 추가 합니다. ( [Cbasekeyframe::가 중 storyboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)를 재정의 합니다.)|
|[CKeyFrame:: AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|전환 후에 storyboard에 키 프레임을 추가 합니다.|
|[CKeyFrame:: AddToStoryboardAtOffset](#addtostoryboardatoffset)|키 프레임을 오프셋에서 storyboard에 추가 합니다.|
|[CKeyFrame:: GetExistingKeyframe](#getexistingkeyframe)|이 키프레임이 종속 되는 키 프레임에 대 한 포인터를 반환 합니다.|
|[CKeyFrame:: GetOffset](#getoffset)|다른 키 프레임의 오프셋을 반환 합니다.|
|[CKeyFrame:: GetTransition](#gettransition)|이 키프레임이 종속 된 전환에 대 한 포인터를 반환 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CKeyFrame:: m_offset](#m_offset)|M_pExistingKeyFrame에 저장 된 키 프레임에서이 키프레임의 오프셋을 지정 합니다.|
|[CKeyFrame:: m_pExistingKeyFrame](#m_pexistingkeyframe)|기존 keframe에 대 한 포인터를 저장 합니다. 이 키프레임은 기존 키 프레임에 대 한 m_offset를 사용 하 여 스토리 보드에 추가 됩니다.|
|[CKeyFrame:: m_pTransition](#m_ptransition)|이 키 프레임에서 시작 하는 전환에 대 한 포인터를 저장 합니다.|

## <a name="remarks"></a>설명

이 클래스는 애니메이션 키 프레임을 구현 합니다. 키프레임은 storyboard 내의 순간을 나타내며 전환의 시작 및 종료 시간을 지정 하는 데 사용할 수 있습니다. 키프레임은 다른 키 프레임을 기반으로 할 수 있으며,이에 대 한 오프셋 (초)을 사용 하거나, 전환을 기반으로 하 여이 전환이 종료 되는 시간을 나타낼 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a> CKeyFrame::가 중 Storyboard

Storyboard에 키 프레임을 추가 합니다.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
스토리 보드에 대 한 포인터입니다.

*bDeepAdd*<br/>
키 프레임 또는 전환을 재귀적으로 추가할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

키프레임이 성공적으로 추가 된 경우 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드는 storyboard에 키 프레임을 추가 합니다. 다른 키 프레임 또는 전환에 의존 하 고 bDeepAdd가 TRUE 인 경우이 메서드는 재귀적으로 추가 하려고 시도 합니다.

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a> CKeyFrame:: AddToStoryboardAfterTransition

전환 후에 storyboard에 키 프레임을 추가 합니다.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
스토리 보드에 대 한 포인터입니다.

*bDeepAdd*<br/>
전환을 재귀적으로 추가할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

키프레임이 성공적으로 추가 된 경우 TRUE입니다.

### <a name="remarks"></a>설명

이 함수는 전환 후에 storyboard에 키프레임을 추가 하기 위해 프레임 워크에서 호출 됩니다.

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a> CKeyFrame:: AddToStoryboardAtOffset

키 프레임을 오프셋에서 storyboard에 추가 합니다.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
스토리 보드에 대 한 포인터입니다.

*bDeepAdd*<br/>
이 키프레임이 재귀적으로 종속 되는 키 프레임을 추가할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

키프레임이 성공적으로 추가 된 경우 TRUE입니다.

### <a name="remarks"></a>설명

이 함수는 프레임 워크에서 오프셋의 storyboard에 키 프레임을 추가 하기 위해 호출 합니다.

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a> CKeyFrame:: CKeyFrame

전환에 종속 되는 키 프레임을 생성 합니다.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>매개 변수

*pTransition*<br/>
전환에 대 한 포인터입니다.

*pKeyframe*<br/>
키 프레임에 대 한 포인터입니다.

*offset*<br/>
PKeyframe 지정 된 키 프레임에서의 오프셋 (초)입니다.

### <a name="remarks"></a>설명

생성 된 키프레임은 지정 된 전환이 끝날 때 storyboard 내에서의 시간을 나타냅니다.

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a> CKeyFrame:: GetExistingKeyframe

이 키프레임이 종속 되는 키 프레임에 대 한 포인터를 반환 합니다.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>반환 값

키 프레임에 대 한 유효한 포인터 이거나,이 키프레임이 다른 키프레임에 종속 되지 않는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 키프레임이 종속 되는 키 프레임에 대 한 접근자입니다.

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a> CKeyFrame:: GetOffset

다른 키 프레임의 오프셋을 반환 합니다.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>반환 값

다른 키 프레임에서의 오프셋 (초)입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 다른 키 프레임에서의 오프셋 (초)을 결정 해야 합니다.

## <a name="ckeyframegettransition"></a><a name="gettransition"></a> CKeyFrame:: GetTransition

이 키프레임이 종속 된 전환에 대 한 포인터를 반환 합니다.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>반환 값

전환에 대 한 유효한 포인터 이거나,이 키프레임이 전환에 의존 하지 않는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 키프레임이 종속 된 전환에 대 한 접근자입니다.

## <a name="ckeyframem_offset"></a><a name="m_offset"></a> CKeyFrame:: m_offset

M_pExistingKeyFrame에 저장 된 키 프레임에서이 키프레임의 오프셋을 지정 합니다.

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a> CKeyFrame:: m_pExistingKeyFrame

기존 keframe에 대 한 포인터를 저장 합니다. 이 키프레임은 기존 키 프레임에 대 한 m_offset를 사용 하 여 스토리 보드에 추가 됩니다.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a> CKeyFrame:: m_pTransition

이 키 프레임에서 시작 하는 전환에 대 한 포인터를 저장 합니다.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
