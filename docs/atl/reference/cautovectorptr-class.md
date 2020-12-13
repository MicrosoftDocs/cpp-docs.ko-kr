---
description: '자세히 알아보기: CAutoVectorPtr 클래스'
title: CAutoVectorPtr 클래스
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: 60e61abb5519043e89266f3f9d9a2f4d9aec138a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152492"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 클래스

이 클래스는 vector new 및 delete 연산자를 사용 하는 스마트 포인터 개체를 나타냅니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
포인터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|생성자입니다.|
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAutoVectorPtr:: Allocate](#allocate)|이 메서드를 호출 하 여가 가리키는 개체의 배열에 필요한 메모리를 할당 `CAutoVectorPtr` 합니다.|
|[CAutoVectorPtr:: Attach](#attach)|기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.|
|[CAutoVectorPtr::D etach](#detach)|포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.|
|[CAutoVectorPtr:: Free](#free)|가 가리키는 개체를 삭제 하려면이 메서드를 호출 `CAutoVectorPtr` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAutoVectorPtr:: operator T *](#operator_t__star)|캐스트 연산자입니다.|
|[CAutoVectorPtr:: operator =](#operator_eq)|할당 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAutoVectorPtr:: m_p](#m_p)|포인터 데이터 멤버 변수입니다.|

## <a name="remarks"></a>설명

이 클래스는 스마트 포인터를 만들고 관리 하는 메서드를 제공 합니다 .이 메서드는 범위를 벗어나면 리소스를 자동으로 해제 하 여 메모리 누수를 방지 하는 데 도움이 됩니다. `CAutoVectorPtr` 는와 유사 `CAutoPtr` 합니다 .이는 `CAutoVectorPtr` [vector new&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) 와 [vector delete&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) 를 사용 하 여 c + + 및 연산자 대신 메모리를 할당 하 고 해제 하는 것뿐입니다 **`new`** **`delete`** . 의 컬렉션 클래스가 필요한 경우 [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) 를 참조 하세요 `CAutoVectorPtr` .

스마트 포인터 클래스 사용에 대 한 예제는 [CAutoPtr](../../atl/reference/cautoptr-class.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a> CAutoVectorPtr:: Allocate

이 메서드를 호출 하 여가 가리키는 개체의 배열에 필요한 메모리를 할당 `CAutoVectorPtr` 합니다.

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>매개 변수

*nElements*<br/>
배열의 요소 수입니다.

### <a name="return-value"></a>반환 값

메모리가 성공적으로 할당 되 면 true를 반환 하 고, 실패 하면 false를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서 [CAutoVectorPtr:: m_p](#m_p) 멤버 변수가 현재 기존 값을 가리키는 경우 어설션 오류가 발생 합니다. 즉, NULL과 같지 않습니다.

## <a name="cautovectorptrattach"></a><a name="attach"></a> CAutoVectorPtr:: Attach

기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
`CAutoVectorPtr`개체는이 포인터의 소유권을 갖습니다.

### <a name="remarks"></a>설명

개체에서 `CAutoVectorPtr` 포인터의 소유권을 가져오는 경우 포인터와 할당 된 모든 데이터가 범위를 벗어나면 자동으로 삭제 됩니다. [CAutoVectorPtr::D etach](#detach) 가 호출 되 면 프로그래머는 할당 된 리소스를 해제 하는 책임을 다시 제공 합니다.

디버그 빌드에서 [CAutoVectorPtr:: m_p](#m_p) 멤버 변수가 현재 기존 값을 가리키는 경우 어설션 오류가 발생 합니다. 즉, NULL과 같지 않습니다.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a> CAutoVectorPtr::CAutoVectorPtr

생성자입니다.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
기존 포인터입니다.

### <a name="remarks"></a>설명

`CAutoVectorPtr`개체는 기존 포인터를 사용 하 여 만들 수 있으며,이 경우 포인터의 소유권을 전송 합니다.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a> CAutoVectorPtr:: ~ CAutoVectorPtr

소멸자입니다.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 해제 합니다. [CAutoVectorPtr:: Free](#free)를 호출 합니다.

## <a name="cautovectorptrdetach"></a><a name="detach"></a> CAutoVectorPtr::D etach

포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.

```
T* Detach() throw();
```

### <a name="return-value"></a>반환 값

포인터의 복사본을 반환 합니다.

### <a name="remarks"></a>설명

포인터의 소유권을 해제 하 고, [CAutoVectorPtr:: m_p](#m_p) 멤버 변수를 NULL로 설정 하 고, 포인터의 복사본을 반환 합니다. 를 호출한 후에는 해당 `Detach` `CAutoVectorPtr` 개체가 이전에 책임이 있는 것으로 간주 되는 할당 된 리소스를 모두 해제 해야 합니다.

## <a name="cautovectorptrfree"></a><a name="free"></a> CAutoVectorPtr:: Free

가 가리키는 개체를 삭제 하려면이 메서드를 호출 `CAutoVectorPtr` 합니다.

```cpp
void Free() throw();
```

### <a name="remarks"></a>설명

가 가리키는 개체가 `CAutoVectorPtr` 해제 되 고 [CAutoVectorPtr:: m_p](#m_p) 멤버 변수가 NULL로 설정 됩니다.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a> CAutoVectorPtr:: m_p

포인터 데이터 멤버 변수입니다.

```
T* m_p;
```

### <a name="remarks"></a>설명

이 멤버 변수는 포인터 정보를 포함 합니다.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a> CAutoVectorPtr:: operator =

할당 연산자입니다.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
포인터입니다.

### <a name="return-value"></a>반환 값

**CAutoVectorPtr \< T >** 에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

할당 연산자는 `CAutoVectorPtr` 현재 포인터에서 개체를 분리 하 고 새 포인터 *p* 를 대신 연결 합니다.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a> CAutoVectorPtr:: operator T *

캐스트 연산자입니다.

```
operator T*() const throw();
```

### <a name="remarks"></a>설명

클래스 템플릿에 정의 된 개체 데이터 형식에 대 한 포인터를 반환 합니다.

## <a name="see-also"></a>참고 항목

[CAutoPtr 클래스](../../atl/reference/cautoptr-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
