---
description: '자세히 알아보기: CHandle 클래스'
title: CHandle 클래스
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 01c3b281daf829bc6488df35114c6cb853640ed1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141676"
---
# <a name="chandle-class"></a>CHandle 클래스

이 클래스는 핸들 개체를 만들고 사용 하기 위한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CHandle
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|생성자입니다.|
|[CHandle:: ~ CHandle](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHandle:: Attach](#attach)|이 메서드를 호출 하 여 `CHandle` 개체를 기존 핸들에 연결 합니다.|
|[CHandle:: Close](#close)|이 메서드를 호출 하 여 `CHandle` 개체를 닫습니다.|
|[CHandle::D etach](#detach)|개체에서 핸들을 분리 하려면이 메서드를 호출 `CHandle` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CHandle:: operator 핸들](#operator_handle)|저장 된 핸들의 값을 반환 합니다.|
|[CHandle:: operator =](#operator_eq)|대입 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CHandle:: m_h](#m_h)|핸들을 저장 하는 멤버 변수입니다.|

## <a name="remarks"></a>설명

`CHandle`개체는 핸들이 필요할 때마다 사용할 수 있습니다. 주요 차이점은 `CHandle` 개체가 자동으로 삭제 됨을 나타내는 것입니다.

> [!NOTE]
> 일부 API 함수는 비어 있거나 잘못 된 핸들로 NULL을 사용 하 고 다른 API 함수는 INVALID_HANDLE_VALUE을 사용 합니다. `CHandle` 는 NULL만 사용 하 고 INVALID_HANDLE_VALUE를 실제 핸들로 처리 합니다. INVALID_HANDLE_VALUE를 반환할 수 있는 API를 호출 하는 경우 [CHandle:: Attach](#attach) 를 호출 하거나 생성자에 전달 하기 전에이 값을 확인 `CHandle` 하 고 대신 NULL을 전달 해야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="chandleattach"></a><a name="attach"></a> CHandle:: Attach

이 메서드를 호출 하 여 `CHandle` 개체를 기존 핸들에 연결 합니다.

```cpp
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>매개 변수

*h*<br/>
`CHandle` 는 핸들 *h* 의 소유권을 갖습니다.

### <a name="remarks"></a>설명

개체를 `CHandle` *h* 핸들에 할당 한 다음, **h. Detach ()** 를 호출 합니다. 빌드 디버그에서 *h* 가 NULL 인 경우에는이 아닌 어설션이 발생 합니다. 핸들의 유효성을 검사 하는 다른 검사는 수행 되지 않습니다.

## <a name="chandlechandle"></a><a name="chandle"></a> CHandle::CHandle

생성자입니다.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>매개 변수

*h*<br/>
기존 핸들 또는 `CHandle` 입니다.

### <a name="remarks"></a>설명

`CHandle`필요에 따라 기존 핸들이 나 개체를 사용 하 여 새 개체를 만듭니다 `CHandle` .

## <a name="chandlechandle"></a><a name="dtor"></a> CHandle:: ~ CHandle

소멸자입니다.

```
~CHandle() throw();
```

### <a name="remarks"></a>설명

`CHandle` [CHandle:: Close](#close)를 호출 하 여 개체를 해제 합니다.

## <a name="chandleclose"></a><a name="close"></a> CHandle:: Close

이 메서드를 호출 하 여 `CHandle` 개체를 닫습니다.

```cpp
void Close() throw();
```

### <a name="remarks"></a>설명

열린 개체 핸들을 닫습니다. 핸들이 이미 호출 된 경우에는 핸들이 NULL 인 경우 `Close` 디버그 빌드에서는로 서 어설션이 발생 합니다.

## <a name="chandledetach"></a><a name="detach"></a> CHandle::D etach

개체에서 핸들을 분리 하려면이 메서드를 호출 `CHandle` 합니다.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>반환 값

분리 중인 핸들을 반환 합니다.

### <a name="remarks"></a>설명

핸들의 소유권을 해제 합니다.

## <a name="chandlem_h"></a><a name="m_h"></a> CHandle:: m_h

핸들을 저장 하는 멤버 변수입니다.

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a> CHandle:: operator =

할당 연산자입니다.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>매개 변수

*h*<br/>
`CHandle` 는 핸들 *h* 의 소유권을 갖습니다.

### <a name="return-value"></a>반환 값

새 개체에 대 한 참조를 반환 합니다 `CHandle` .

### <a name="remarks"></a>설명

`CHandle`현재 개체가 핸들을 포함 하는 경우 닫힙니다. `CHandle`전달 되는 개체의 핸들 참조는 NULL로 설정 됩니다. 이렇게 하면 두 `CHandle` 개체에 동일한 활성 핸들이 포함 되지 않습니다.

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a> CHandle:: operator 핸들

저장 된 핸들의 값을 반환 합니다.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>설명

[CHandle:: m_h](#m_h)에 저장 된 값을 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
