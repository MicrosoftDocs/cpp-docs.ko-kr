---
description: '자세히 알아보기: CBaseKeyFrame 클래스'
title: CBaseKeyFrame 클래스
ms.date: 11/04/2016
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
ms.openlocfilehash: 0bebd91183eab9be71e8df4928dc621565718cb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261259"
---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame 클래스

키프레임의 기본 기능을 구현합니다.

## <a name="syntax"></a>구문

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CBaseKeyFrame:: CBaseKeyFrame](#cbasekeyframe)|키 프레임을 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CBaseKeyFrame::가 중 Storyboard](#addtostoryboard)|Storyboard에 키 프레임을 추가 합니다.|
|[CBaseKeyFrame:: GetAnimationKeyframe](#getanimationkeyframe)|내부 키 프레임 값을 반환 합니다.|
|[CBaseKeyFrame:: IsAdded 됨](#isadded)|키프레임이 storyboard에 추가 되었는지 여부를 나타냅니다.|
|[CBaseKeyFrame:: Iskey프레임 Atoffset](#iskeyframeatoffset)|키 프레임을 오프셋에서 storyboard에 추가할지, 아니면 전환 후에 추가할지를 지정 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CBaseKeyFrame:: m_bAdded](#m_badded)|이 키프레임이 storyboard에 추가 되었는지 여부를 지정 합니다.|
|[CBaseKeyFrame:: m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|이 키프레임이 다른 기존 프레임 보드의 오프셋에서 또는 일부 전환의 끝에서 storyboard에 추가 되어야 하는지 여부를 지정 합니다.|
|[CBaseKeyFrame:: m_keyframe](#m_keyframe)|Windows 애니메이션 API 키프레임을 나타냅니다. 키프레임이 초기화 되지 않은 경우 UI_ANIMATION_KEYFRAME_STORYBOARD_START 미리 정의 된 값으로 설정 됩니다.|

## <a name="remarks"></a>설명

UI_ANIMATION_KEYFRAME 변수를 캡슐화 합니다. 모든 키 프레임 구현에 대 한 기본 클래스로 사용 됩니다. 키프레임은 storyboard 내의 순간을 나타내며 전환의 시작 및 종료 시간을 지정 하는 데 사용할 수 있습니다. 지정 된 전환 후에 추가 된 키 프레임, 즉 지정 된 오프셋 (시간)에 스토리 보드에 추가 된 두 가지 유형의 키 프레임 및 키프레임이 있습니다. 애니메이션을 시작 하기 전에 일부 전환의 기간을 알 수 없기 때문에 일부 키 프레임의 실제 값은 런타임에만 결정 됩니다. 키프레임은 키프레임에 따라 달라 지는 전환을 종속 시킬 수 있기 때문에 키 프레임 체인을 빌드할 때 무한 재귀을 방지 하는 것이 중요 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a> CBaseKeyFrame::가 중 Storyboard

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
이 매개 변수가 TRUE이 고 추가 되는 키프레임이 일부 다른 키 프레임 또는 전환에 따라 달라 지는 경우이 메서드는 먼저이 키 프레임을 추가 하거나 storyboard에 전환을 추가 하려고 시도 합니다.

### <a name="return-value"></a>반환 값

키프레임이 storyboard에 성공적으로 추가 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 storyboard에 키 프레임을 추가 하기 위해 호출 됩니다.

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a> CBaseKeyFrame:: CBaseKeyFrame

키 프레임을 생성 합니다.

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a> CBaseKeyFrame:: GetAnimationKeyframe

내부 키 프레임 값을 반환 합니다.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>반환 값

현재 키 프레임입니다. 기본값은 UI_ANIMATION_KEYFRAME_STORYBOARD_START입니다.

### <a name="remarks"></a>설명

기본 키 프레임 값에 대 한 접근자입니다.

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a> CBaseKeyFrame:: IsAdded 됨

키프레임이 storyboard에 추가 되었는지 여부를 나타냅니다.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>반환 값

키프레임이 storyboard에 추가 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

IsAdded 된 기본 클래스에서 항상 TRUE를 반환 하지만 파생 클래스에서 재정의 됩니다.

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a> CBaseKeyFrame:: Iskey프레임 Atoffset

키 프레임을 오프셋에서 storyboard에 추가할지, 아니면 전환 후에 추가할지를 지정 합니다.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>반환 값

지정 된 특정 오프셋에서 키프레임을 storyboard에 추가 해야 하는 경우 TRUE입니다. 전환 후 키프레임이 storyboard에 추가 되어야 하면 FALSE입니다.

### <a name="remarks"></a>설명

키 프레임을 오프셋 시 storyboard에 추가할지 여부를 지정 합니다. 오프셋 또는 전환은 파생 클래스에서 지정 해야 합니다.

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a> CBaseKeyFrame:: m_bAdded

이 키프레임이 storyboard에 추가 되었는지 여부를 지정 합니다.

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a> CBaseKeyFrame:: m_bIsKeyframeAtOffset

이 키프레임이 다른 기존 프레임 보드의 오프셋에서 또는 일부 전환의 끝에서 storyboard에 추가 되어야 하는지 여부를 지정 합니다.

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a> CBaseKeyFrame:: m_keyframe

Windows 애니메이션 API 키프레임을 나타냅니다. 키프레임이 초기화 되지 않은 경우 UI_ANIMATION_KEYFRAME_STORYBOARD_START 미리 정의 된 값으로 설정 됩니다.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
