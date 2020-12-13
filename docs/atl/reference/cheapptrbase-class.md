---
description: '자세히 알아보기: CHeapPtrBase 클래스'
title: CHeapPtrBase 클래스
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: 6186f68066f4c159c16c458f9f00725478aa98a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141637"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase 클래스

이 클래스는 여러 스마트 힙 포인터 클래스의 기본을 형성 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
힙에 저장할 개체 형식입니다.

*할당자*<br/>
사용할 메모리 할당 클래스입니다. 기본적으로 CRT 루틴은 메모리를 할당 하 고 해제 하는 데 사용 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHeapPtrBase:: AllocateBytes](#allocatebytes)|이 메서드를 호출 하 여 메모리를 할당 합니다.|
|[CHeapPtrBase:: Attach](#attach)|기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.|
|[CHeapPtrBase::D etach](#detach)|포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.|
|[CHeapPtrBase:: Free](#free)|가 가리키는 개체를 삭제 하려면이 메서드를 호출 `CHeapPtrBase` 합니다.|
|[CHeapPtrBase:: ReallocateBytes](#reallocatebytes)|메모리를 다시 할당 하려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CHeapPtrBase:: operator T *](#operator_t_star)|캐스트 연산자입니다.|
|[CHeapPtrBase:: operator &](#operator_amp)|& 연산자|
|[CHeapPtrBase:: operator->](#operator_ptr)|멤버 포인터 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CHeapPtrBase:: m_pData](#m_pdata)|포인터 데이터 멤버 변수입니다.|

## <a name="remarks"></a>설명

이 클래스는 여러 스마트 힙 포인터 클래스의 기본을 형성 합니다. 파생 클래스 (예: [CHeapPtr](../../atl/reference/cheapptr-class.md) 및 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md))는 자체 생성자와 연산자를 추가 합니다. 구현 예제는 이러한 클래스를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a> CHeapPtrBase:: AllocateBytes

이 메서드를 호출 하 여 메모리를 할당 합니다.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
할당할 메모리의 바이트 수입니다.

### <a name="return-value"></a>반환 값

메모리가 성공적으로 할당 되 면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서 [CHeapPtrBase:: m_pData](#m_pdata) 멤버 변수가 현재 기존 값을 가리키는 경우 어설션 오류가 발생 합니다. 즉, NULL과 같지 않습니다.

## <a name="cheapptrbaseattach"></a><a name="attach"></a> CHeapPtrBase:: Attach

기존 포인터의 소유권을 사용 하려면이 메서드를 호출 합니다.

```cpp
void Attach(T* pData) throw();
```

### <a name="parameters"></a>매개 변수

*pData*<br/>
`CHeapPtrBase`개체는이 포인터의 소유권을 갖습니다.

### <a name="remarks"></a>설명

개체에서 `CHeapPtrBase` 포인터의 소유권을 가져오는 경우 포인터와 할당 된 모든 데이터가 범위를 벗어나면 자동으로 삭제 됩니다.

디버그 빌드에서 [CHeapPtrBase:: m_pData](#m_pdata) 멤버 변수가 현재 기존 값을 가리키는 경우 어설션 오류가 발생 합니다. 즉, NULL과 같지 않습니다.

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a> CHeapPtrBase:: ~ CHeapPtrBase

소멸자입니다.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="cheapptrbasedetach"></a><a name="detach"></a> CHeapPtrBase::D etach

포인터의 소유권을 해제 하려면이 메서드를 호출 합니다.

```
T* Detach() throw();
```

### <a name="return-value"></a>반환 값

포인터의 복사본을 반환 합니다.

### <a name="remarks"></a>설명

포인터의 소유권을 해제 하 고, [CHeapPtrBase:: m_pData](#m_pdata) 멤버 변수를 NULL로 설정 하 고, 포인터의 복사본을 반환 합니다.

## <a name="cheapptrbasefree"></a><a name="free"></a> CHeapPtrBase:: Free

가 가리키는 개체를 삭제 하려면이 메서드를 호출 `CHeapPtrBase` 합니다.

```cpp
void Free() throw();
```

### <a name="remarks"></a>설명

가 가리키는 개체가 `CHeapPtrBase` 해제 되 고 [CHeapPtrBase:: m_pData](#m_pdata) 멤버 변수가 NULL로 설정 됩니다.

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a> CHeapPtrBase:: m_pData

포인터 데이터 멤버 변수입니다.

```
T* m_pData;
```

### <a name="remarks"></a>설명

이 멤버 변수는 포인터 정보를 포함 합니다.

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a> CHeapPtrBase:: operator &amp;

& 연산자

```
T** operator&() throw();
```

### <a name="return-value"></a>반환 값

개체가 가리키는 개체의 주소를 반환 `CHeapPtrBase` 합니다.

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a> CHeapPtrBase:: operator-&gt;

멤버 포인터 연산자입니다.

```
T* operator->() const throw();
```

### <a name="return-value"></a>반환 값

[CHeapPtrBase:: m_pData](#m_pdata) 멤버 변수의 값을 반환 합니다.

### <a name="remarks"></a>설명

이 연산자를 사용 하 여 개체가 가리키는 클래스에서 메서드를 호출 `CHeapPtrBase` 합니다. 디버그 빌드에서는가 NULL을 가리키는 경우 어설션 오류가 발생 `CHeapPtrBase` 합니다.

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a> CHeapPtrBase:: operator T *

캐스트 연산자입니다.

```
operator T*() const throw();
```

### <a name="remarks"></a>설명

[CHeapPtrBase:: m_pData](#m_pdata)을 반환 합니다.

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a> CHeapPtrBase:: ReallocateBytes

메모리를 다시 할당 하려면이 메서드를 호출 합니다.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*nBytes*<br/>
할당할 새 메모리 양 (바이트)입니다.

### <a name="return-value"></a>반환 값

메모리가 성공적으로 할당 되 면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

## <a name="see-also"></a>참고 항목

[CHeapPtr 클래스](../../atl/reference/cheapptr-class.md)<br/>
[CComHeapPtr 클래스](../../atl/reference/ccomheapptr-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
