---
description: '자세히 알아보기: CComGITPtr 클래스'
title: CComGITPtr 클래스
ms.date: 11/04/2016
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: a457c0dea1679b177b72318d636c856334c85e36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146642"
---
# <a name="ccomgitptr-class"></a>CComGITPtr 클래스

이 클래스는 인터페이스 포인터와 GIT (전역 인터페이스 테이블)를 처리 하기 위한 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
GIT에 저장 되는 인터페이스 포인터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|생성자입니다.|
|[CComGITPtr:: ~ CComGITPtr](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComGITPtr:: Attach](#attach)|이 메서드를 호출 하 여 전역 인터페이스 테이블 (GIT)에 인터페이스 포인터를 등록 합니다.|
|[CComGITPtr:: CopyTo](#copyto)|이 메서드를 호출 하 여 전역 인터페이스 테이블 (GIT)의 인터페이스를 전달 된 포인터로 복사 합니다.|
|[CComGITPtr::D etach](#detach)|이 메서드를 호출 하 여 개체에서 인터페이스의 연결을 해제 `CComGITPtr` 합니다.|
|[CComGITPtr:: GetCookie](#getcookie)|개체에서 쿠키를 반환 하려면이 메서드를 호출 `CComGITPtr` 합니다.|
|[CComGITPtr:: Revoke](#revoke)|GIT (전역 인터페이스 테이블)에서 인터페이스를 제거 하려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CComGITPtr:: operator DWORD](#operator_dword)|개체에서 쿠키를 반환 합니다 `CComGITPtr` .|
|[CComGITPtr:: operator =](#operator_eq)|대입 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComGITPtr:: m_dwCookie](#m_dwcookie)|쿠키입니다.|

## <a name="remarks"></a>설명

자유 스레드된 마샬러를 집계 하 고 다른 개체에서 얻은 인터페이스 포인터를 사용 해야 하는 개체는 인터페이스가 올바르게 마샬링되는 추가 단계를 수행 해야 합니다. 일반적으로이 작업은 GIT에 인터페이스 포인터를 저장 하 고 사용할 때마다 GIT에서 포인터를 가져오는 작업을 포함 합니다. 클래스는 `CComGITPtr` GIT에 저장 된 인터페이스 포인터를 사용할 수 있도록 제공 됩니다.

> [!NOTE]
> 전역 인터페이스 테이블 기능은 Windows 95 (DCOM 버전 1.1 이상, Windows 98, Windows NT 4.0 서비스 팩 3 이상 및 Windows 2000) 에서만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccomgitptrattach"></a><a name="attach"></a> CComGITPtr:: Attach

이 메서드를 호출 하 여 전역 인터페이스 테이블 (GIT)에 인터페이스 포인터를 등록 합니다.

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
GIT에 추가할 인터페이스 포인터입니다.

*dwCookie*<br/>
인터페이스 포인터를 식별 하는 데 사용 되는 쿠키입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 GIT가 유효 하지 않거나 쿠키가 NULL과 같은 경우 어설션 오류가 발생 합니다.

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a> CComGITPtr::CComGITPtr

생성자입니다.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 GIT (전역 인터페이스 테이블)에 저장할 인터페이스 포인터입니다.

*git*<br/>
진행 기존 개체에 대 한 참조 `CComGITPtr` 입니다.

*dwCookie*<br/>
진행 인터페이스 포인터를 식별 하는 데 사용 되는 쿠키입니다.

*rv*<br/>
진행 데이터를 `CComGITPtr` 이동할 원본 개체입니다.

### <a name="remarks"></a>설명

`CComGITPtr`선택적으로 기존 개체를 사용 하 여 새 개체를 만듭니다 `CComGITPtr` .

*Rv* 를 활용 하는 생성자는 이동 생성자입니다. 원본, *rv* 에서 데이터가 이동 된 다음 *rv* 가 지워집니다.

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a> CComGITPtr:: ~ CComGITPtr

소멸자입니다.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>설명

[CComGITPtr:: Revoke](#revoke)를 사용 하 여 전역 인터페이스 테이블 (GIT)에서 인터페이스를 제거 합니다.

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a> CComGITPtr:: CopyTo

이 메서드를 호출 하 여 전역 인터페이스 테이블 (GIT)의 인터페이스를 전달 된 포인터로 복사 합니다.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>매개 변수

*페이지*<br/>
인터페이스를 받을 포인터입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

GIT의 인터페이스가 전달 된 포인터에 복사 됩니다. 더 이상 필요 하지 않은 경우 호출자가 포인터를 해제 해야 합니다.

## <a name="ccomgitptrdetach"></a><a name="detach"></a> CComGITPtr::D etach

이 메서드를 호출 하 여 개체에서 인터페이스의 연결을 해제 `CComGITPtr` 합니다.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>반환 값

개체에서 쿠키를 반환 합니다 `CComGITPtr` .

### <a name="remarks"></a>설명

[CComGITPtr:: Revoke](#revoke)를 사용 하 여 GIT에서 인터페이스를 제거 하는 것은 호출자의 것입니다.

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a> CComGITPtr:: GetCookie

개체에서 쿠키를 반환 하려면이 메서드를 호출 `CComGITPtr` 합니다.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>반환 값

쿠키를 반환 합니다.

### <a name="remarks"></a>설명

쿠키는 인터페이스 및 해당 위치를 식별 하는 데 사용 되는 변수입니다.

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a> CComGITPtr:: m_dwCookie

쿠키입니다.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>설명

쿠키는 인터페이스 및 해당 위치를 식별 하는 데 사용 되는 멤버 변수입니다.

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a> CComGITPtr:: operator =

할당 연산자입니다.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 인터페이스에 대 한 포인터입니다.

*git*<br/>
[in] `CComGITPtr` 개체에 대한 참조입니다.

*dwCookie*<br/>
진행 인터페이스 포인터를 식별 하는 데 사용 되는 쿠키입니다.

*rv*<br/>
진행 `CComGITPtr` 데이터를 이동할입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체를 반환 `CComGITPtr` 합니다.

### <a name="remarks"></a>설명

`CComGITPtr`기존 개체 또는 전역 인터페이스 테이블에 대 한 참조에서 개체에 새 값을 할당 합니다.

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a> CComGITPtr:: operator DWORD

개체와 연결 된 쿠키를 반환 합니다 `CComGITPtr` .

```
operator DWORD() const;
```

### <a name="remarks"></a>설명

쿠키는 인터페이스 및 해당 위치를 식별 하는 데 사용 되는 변수입니다.

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a> CComGITPtr:: Revoke

GIT (전역 인터페이스 테이블)에서 현재 인터페이스를 제거 하려면이 메서드를 호출 합니다.

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

GIT에서 인터페이스를 제거 합니다.

## <a name="see-also"></a>참고 항목

[자유 스레드된 마샬러](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[아파트에서 인터페이스 액세스](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[전역 인터페이스 테이블을 사용 하는 경우](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
