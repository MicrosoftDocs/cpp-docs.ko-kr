---
description: '자세히 알아보기: CMFCAcceleratorKey 클래스'
title: CMFCAcceleratorKey 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: cb7fc24c4cb4d092c5f109ad892b3778d74a906f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336610"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey 클래스

가상 키 매핑 및 서식을 구현 하는 도우미 클래스입니다.

## <a name="syntax"></a>구문

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCAcceleratorKey:: CMFCAcceleratorKey](#cmfcacceleratorkey)|`CMFCAcceleratorKey` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCAcceleratorKey:: Format](#format)|가속 구조체를 시각적 표현으로 변환 합니다.|
|[CMFCAcceleratorKey:: SetAccelerator](#setaccelerator)|개체에 대 한 바로 가기 키를 설정 합니다 `CMFCAcceleratorKey` .|

## <a name="remarks"></a>설명

액셀러레이터 키를 바로 가기 키 라고도 합니다. 사용자가 입력 하는 바로 가기 키를 표시 하려면 [CMFCAcceleratorKeyAssignCtrl 클래스](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 에서 키보드 바로 가기 키 (예: Alt + Shift + s)를 "Alt + Shift + s"와 같은 사용자 지정 텍스트 형식에 매핑합니다. 각 `CMFCAcceleratorKey` 개체는 단일 바로 가기 키를 텍스트 형식에 매핑합니다.

바로 가기 키 및 액셀러레이터 키 테이블을 사용 하는 방법에 대 한 자세한 내용은 [CKeyboardManager 클래스](../../mfc/reference/ckeyboardmanager-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 개체를 생성 하는 방법과 `CMFCAcceleratorKey` 해당 메서드를 사용 하는 방법을 보여 줍니다 `Format` .

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>요구 사항

**헤더:** afxacceleratorkey

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a> CMFCAcceleratorKey:: CMFCAcceleratorKey

[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) 개체를 생성 합니다.

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>매개 변수

*lpAccel*<br/>
진행 바로 가기 키에 대 한 포인터입니다.

### <a name="remarks"></a>설명

를 만들 때 바로 가기 키를 제공 하지 않는 경우 `CMFCAccleratorKey` [CMFCAcceleratorKey:: setaccelerator](#setaccelerator) 메서드를 사용 하 여 바로 가기 키를 개체에 연결 `CMFCAcceleratorKey` 합니다.

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a> CMFCAcceleratorKey:: Format

가속 구조체를 연결 된 문자열 값으로 변환 합니다.

```cpp
void Format(CString& str) const;
```

### <a name="parameters"></a>매개 변수

*str*<br/>
제한이 `CString` 메서드가 번역 된 바로 가기 키를 작성 하는 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드는 연결 된 바로 가기 키의 문자열 형식을 검색 합니다. 생성자 또는 메서드 [CMFCAcceleratorKey:: SetAccelerator](#setaccelerator)를 사용 하 여 [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) 개체의 문자열 형식을 설정할 수 있습니다.

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a> CMFCAcceleratorKey:: SetAccelerator

[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) 개체에 대 한 바로 가기 키를 설정 합니다.

```cpp
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>매개 변수

*lpAccel*<br/>
진행 바로 가기 키에 대 한 포인터입니다.

### <a name="remarks"></a>설명

를 `CMFCAcceleratorKey` 만들 때 바로 가기 키를 제공 하지 않은 경우이 메서드를 사용 하 여에 대 한 바로 가기 키를 설정 합니다 `CMFCAcceleratorKey` .

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 클래스](../../mfc/reference/ckeyboardmanager-class.md)
