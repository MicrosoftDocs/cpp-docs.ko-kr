---
description: '자세히 알아보기: CComQIPtr 클래스'
title: CComQIPtr 클래스
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: e5af938cd7b2bbae3b091eac5323d3455ce1cf02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142326"
---
# <a name="ccomqiptr-class"></a>CComQIPtr 클래스

COM 인터페이스 포인터를 관리 하기 위한 스마트 포인터 클래스입니다.

## <a name="syntax"></a>구문

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
저장할 포인터의 형식을 지정 하는 COM 인터페이스입니다.

*piid*<br/>
*T* 의 IID에 대 한 포인터입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComQIPtr:: CComQIPtr](#ccomqiptr)|생성자입니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CComQIPtr:: operator =](#operator_eq)|멤버 포인터에 대 한 포인터를 할당 합니다.|

## <a name="remarks"></a>설명

ATL은 `CComQIPtr` 및 [CComPtr](../../atl/reference/ccomptr-class.md) 를 사용 하 여 COM 인터페이스 포인터를 관리 합니다. 둘 다 [ccomptrbase](../../atl/reference/ccomptrbase-class.md)에서 파생 됩니다. 두 클래스 모두 및에 대 한 호출을 통해 자동 참조 계산을 수행 `AddRef` `Release` 합니다. 오버 로드 된 연산자는 포인터 연산을 처리 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>요구 사항

**헤더:** comcli .h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a> CComQIPtr:: CComQIPtr

생성자입니다.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>매개 변수

*lp*<br/>
인터페이스 포인터를 초기화 하는 데 사용 됩니다.

*T*<br/>
COM 인터페이스입니다.

*piid*<br/>
*T* 의 IID에 대 한 포인터입니다.

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a> CComQIPtr:: operator =

할당 연산자입니다.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>매개 변수

*lp*<br/>
인터페이스 포인터를 초기화 하는 데 사용 됩니다.

*T*<br/>
COM 인터페이스입니다.

*piid*<br/>
*T* 의 IID에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체에 대 한 포인터를 반환 `CComQIPtr` 합니다.

## <a name="see-also"></a>참고 항목

[CComPtr:: CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr:: CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase 클래스](../../atl/reference/ccomptrbase-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits 클래스](../../atl/reference/ccomqiptrelementtraits-class.md)
