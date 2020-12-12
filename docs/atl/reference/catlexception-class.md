---
description: '자세한 정보: CAtlException 클래스'
title: CAtlException 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: b6d788bc8d852fa0b8d091682ff7740aa4ebbbed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147474"
---
# <a name="catlexception-class"></a>CAtlException 클래스

이 클래스는 ATL 예외를 정의 합니다.

## <a name="syntax"></a>구문

```cpp
class CAtlException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[오류:: catlexception](#catlexception)|생성자입니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAtlException:: operator HRESULT](#operator_hresult)|현재 개체를 HRESULT 값으로 캐스팅 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAtlException:: m_hr](#m_hr)|개체에 의해 생성 되 고 오류 조건을 저장 하는 데 사용 되는 HRESULT 형식의 변수입니다.|

## <a name="remarks"></a>설명

`CAtlException`개체는 ATL 작업과 관련 된 예외 조건을 나타냅니다. 클래스에는 예외 `CAtlException` 에 대 한 이유를 나타내는 상태 코드를 저장 하는 공용 데이터 멤버와 예외가 HRESULT 인 것 처럼 처리 하는 데 사용할 수 있는 캐스트 연산자가 포함 되어 있습니다.

일반적으로 `AtlThrow` 개체를 직접 만들지 않고를 호출 합니다 `CAtlException` .

## <a name="requirements"></a>요구 사항

**헤더:** a. h 제외

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a> 오류:: catlexception

생성자입니다.

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>매개 변수

*시간*<br/>
HRESULT 오류 코드입니다.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a> CAtlException:: operator HRESULT

현재 개체를 HRESULT 값으로 캐스팅 합니다.

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a> CAtlException:: m_hr

HRESULT 데이터 멤버입니다.

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>설명

오류 조건을 저장 하는 데이터 멤버입니다. HRESULT 값은 [catlexception:: catlexception](#catlexception)생성자에 의해 설정 됩니다.

## <a name="see-also"></a>참고 항목

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
