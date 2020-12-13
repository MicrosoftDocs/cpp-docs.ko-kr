---
description: '자세히 알아보기: CAutoPtr 클래스'
title: CAutoPtr 클래스
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: ebfa4fc7d0c4557801e351e5705aa990860b2fa8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147175"
---
# <a name="cautoptr-class"></a>CAutoPtr 클래스

이 클래스는 스마트 포인터 개체를 나타냅니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>매개 변수

*T*<br/>
포인터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|생성자입니다.|
|[CAutoPtr:: ~ CAutoPtr](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAutoPtr:: Attach](#attach)|기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.|
|[CAutoPtr::D etach](#detach)|포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.|
|[CAutoPtr:: Free](#free)|가 가리키는 개체를 삭제 하려면이 메서드를 호출 `CAutoPtr` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAutoPtr:: operator T *](#operator_t_star)|캐스트 연산자입니다.|
|[CAutoPtr:: operator =](#operator_eq)|할당 연산자입니다.|
|[CAutoPtr:: operator->](#operator_ptr)|멤버 포인터 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAutoPtr:: m_p](#m_p)|포인터 데이터 멤버 변수입니다.|

## <a name="remarks"></a>설명

이 클래스는 스마트 포인터를 만들고 관리 하는 메서드를 제공 합니다 .이 메서드는 범위를 벗어나면 리소스를 자동으로 해제 하 여 메모리 누수를 방지 하는 데 도움이 됩니다.

추가, `CAutoPtr` 의 복사 생성자 및 대입 연산자는 포인터의 소유권을 이전 하 여 소스 포인터를 대상 포인터로 복사 하 고 소스 포인터를 NULL로 설정 합니다. 따라서 두 개체가 같은 포인터를 저장 하는 것은 불가능 하므로 `CAutoPtr` 동일한 포인터를 두 번 삭제할 가능성이 줄어듭니다.

`CAutoPtr` 는 또한 포인터의 컬렉션 만들기를 간소화 합니다. 컬렉션 클래스를 파생 시키고 소멸자를 재정의 하는 대신 개체의 컬렉션을 만드는 것이 더 간단 `CAutoPtr` 합니다. 컬렉션을 삭제 하면 `CAutoPtr` 개체가 범위를 벗어난 후 자동으로 삭제 됩니다.

[CHeapPtr](../../atl/reference/cheapptr-class.md) 및 Variant는 `CAutoPtr` c + + 및 연산자 대신 다른 힙 함수를 사용 하 여 메모리를 할당 하 고 해제 한다는 점을 제외 하 고와 동일한 방식으로 작동 **`new`** **`delete`** 합니다. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) 는와 유사 `CAutoPtr` 합니다 .이는 **vector new []** 와 **vector delete []** 를 사용 하 여 메모리를 할당 하 고 해제 하는 것뿐입니다.

스마트 포인터의 배열 또는 목록이 필요한 경우에도 [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) 및 [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a> CAutoPtr:: Attach

기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
`CAutoPtr`개체는이 포인터의 소유권을 갖습니다.

### <a name="remarks"></a>설명

개체에서 `CAutoPtr` 포인터의 소유권을 가져오는 경우 포인터와 할당 된 모든 데이터가 범위를 벗어나면 자동으로 삭제 됩니다. [CAutoPtr::D etach](#detach) 가 호출 되 면 프로그래머는 할당 된 리소스를 해제 하는 책임을 다시 제공 합니다.

디버그 빌드에서 [CAutoPtr:: m_p](#m_p) 데이터 멤버가 현재 기존 값을 가리키는 경우 어설션 오류가 발생 합니다. 즉, NULL과 같지 않습니다.

### <a name="example"></a>예제

[CAutoPtr 개요](../../atl/reference/cautoptr-class.md)의 예제를 참조 하세요.

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a> CAutoPtr::CAutoPtr

생성자입니다.

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
기존 포인터입니다.

*TSrc*<br/>
다른에서 관리 하는 형식으로 `CAutoPtr` , 현재 개체를 초기화 하는 데 사용 됩니다.

### <a name="remarks"></a>설명

`CAutoPtr`개체는 기존 포인터를 사용 하 여 만들 수 있으며,이 경우 포인터의 소유권을 전송 합니다.

### <a name="example"></a>예제

[CAutoPtr 개요](../../atl/reference/cautoptr-class.md)의 예제를 참조 하세요.

## <a name="cautoptrcautoptr"></a><a name="dtor"></a> CAutoPtr:: ~ CAutoPtr

소멸자입니다.

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 해제 합니다. [CAutoPtr:: Free](#free)를 호출 합니다.

## <a name="cautoptrdetach"></a><a name="detach"></a> CAutoPtr::D etach

포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>반환 값

포인터의 복사본을 반환 합니다.

### <a name="remarks"></a>설명

포인터의 소유권을 해제 하 고, [CAutoPtr:: m_p](#m_p) 데이터 멤버 변수를 NULL로 설정 하 고, 포인터의 복사본을 반환 합니다. 를 호출한 후에는 `Detach` 개체가 이전에 reponsibility으로 가정 된 할당 된 리소스를 해제 합니다 `CAutoPtr` .

### <a name="example"></a>예제

[CAutoPtr 개요](../../atl/reference/cautoptr-class.md)의 예제를 참조 하세요.

## <a name="cautoptrfree"></a><a name="free"></a> CAutoPtr:: Free

가 가리키는 개체를 삭제 하려면이 메서드를 호출 `CAutoPtr` 합니다.

```cpp
void Free() throw();
```

### <a name="remarks"></a>설명

가 가리키는 개체가 `CAutoPtr` 해제 되 고 [CAutoPtr:: m_p](#m_p) 데이터 멤버 변수가 NULL로 설정 됩니다.

## <a name="cautoptrm_p"></a><a name="m_p"></a> CAutoPtr:: m_p

포인터 데이터 멤버 변수입니다.

```cpp
T* m_p;
```

### <a name="remarks"></a>설명

이 멤버 변수는 포인터 정보를 포함 합니다.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a> CAutoPtr:: operator =

할당 연산자입니다.

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>매개 변수

*®*<br/>
포인터입니다.

*TSrc*<br/>
클래스 형식입니다.

### <a name="return-value"></a>반환 값

**CAutoPtr \< T >** 에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

할당 연산자는 `CAutoPtr` 현재 포인터에서 개체를 분리 하 고 새 포인터 *p* 를 대신 연결 합니다.

### <a name="example"></a>예제

[CAutoPtr 개요](../../atl/reference/cautoptr-class.md)의 예제를 참조 하세요.

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a> CAutoPtr:: operator-&gt;

멤버 포인터 연산자입니다.

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>반환 값

[CAutoPtr:: m_p](#m_p) 데이터 멤버 변수의 값을 반환 합니다.

### <a name="remarks"></a>설명

이 연산자를 사용 하 여 개체가 가리키는 클래스에서 메서드를 호출 `CAutoPtr` 합니다. 디버그 빌드에서는가 NULL을 가리키는 경우 어설션 오류가 발생 `CAutoPtr` 합니다.

### <a name="example"></a>예제

[CAutoPtr 개요](../../atl/reference/cautoptr-class.md)의 예제를 참조 하세요.

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a> CAutoPtr:: operator T *

캐스트 연산자입니다.

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>반환 값

클래스 템플릿에 정의 된 개체 데이터 형식에 대 한 포인터를 반환 합니다.

### <a name="example"></a>예제

[CAutoPtr 개요](../../atl/reference/cautoptr-class.md)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CHeapPtr 클래스](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr 클래스](../../atl/reference/cautovectorptr-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
