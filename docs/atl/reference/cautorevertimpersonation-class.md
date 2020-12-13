---
description: '자세히 알아보기: CAutoRevertImpersonation 클래스'
title: CAutoRevertImpersonation 클래스
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: 48009a4d146866d36eebc75ada8f9ae12058287a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147084"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation 클래스

이 클래스는 범위를 벗어나면 [CAccessToken](../../atl/reference/caccesstoken-class.md) 개체를 가장 비 가장 상태로 되돌립니다.

## <a name="syntax"></a>구문

```
class CAutoRevertImpersonation
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|개체를 생성 합니다. `CAutoRevertImpersonation`|
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|개체를 소멸 시키고 액세스 토큰 가장을 되돌립니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAutoRevertImpersonation:: Attach](#attach)|액세스 토큰의 가장 변경할지를 자동화 합니다.|
|[CAutoRevertImpersonation::D etach](#detach)|자동 가장 변경할지를 취소 합니다.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|이 개체와 연결 된 현재 액세스 토큰을 검색 합니다.|

## <a name="remarks"></a>설명

[액세스 토큰](/windows/win32/SecAuthZ/access-tokens) 은 프로세스나 스레드의 보안 컨텍스트를 설명 하 고 Windows NT 또는 windows 2000 시스템에 로그온 한 각 사용자에 게 할당 되는 개체입니다. 이러한 액세스 토큰은 클래스를 사용 하 여 나타낼 수 있습니다 `CAccessToken` .

액세스 토큰을 가장 해야 하는 경우도 있습니다. 이 클래스는 편의를 위해 제공 되지만 액세스 토큰의 가장을 수행 하지 않습니다. 자동 변경할지 가장 되지 않은 상태로만 수행 됩니다. 토큰 액세스 가장은 여러 가지 방법으로 수행 될 수 있기 때문입니다.

Windows의 액세스 제어 모델에 대 한 소개는 Windows SDK [Access Control](/windows/win32/SecAuthZ/access-control) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a> CAutoRevertImpersonation:: Attach

액세스 토큰의 가장 변경할지를 자동화 합니다.

```cpp
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>매개 변수

*툴*<br/>
자동으로 되돌릴 [CAccessToken](../../atl/reference/caccesstoken-class.md) 개체의 주소입니다.

### <a name="remarks"></a>설명

이 메서드는 [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) 개체가 NULL 포인터를 사용 하 여 생성 된 경우 `CAccessToken` 또는 [Detach](#detach) 가 이전에 호출 된 경우에만 사용 해야 합니다. 간단한 경우에는이 메서드를 사용할 필요가 없습니다.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a> CAutoRevertImpersonation::CAutoRevertImpersonation

`CAutoRevertImpersonation` 개체를 생성합니다.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>매개 변수

*툴*<br/>
자동으로 되돌릴 [CAccessToken](../../atl/reference/caccesstoken-class.md) 개체의 주소입니다.

### <a name="remarks"></a>설명

액세스 토큰의 실제 가장은 개체를 만들기 전과 별도로 수행 해야 합니다 `CAutoRevertImpersonation` . 이 가장은 `CAutoRevertImpersonation` 개체가 범위를 벗어날 때 자동으로 되돌려집니다.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a> CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

개체를 소멸 시키고 액세스 토큰 가장을 되돌립니다.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>설명

생성 시 또는 [연결](#attach) 메서드를 통해 제공 된 [CAccessToken](../../atl/reference/caccesstoken-class.md) 개체에 현재 적용 되는 모든 가장을 되돌립니다. `CAccessToken`가 연결 되어 있지 않으면 소멸자는 영향을 주지 않습니다.

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a> CAutoRevertImpersonation::D etach

자동 가장 변경할지를 취소 합니다.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>반환 값

이전에 연결 된 [CAccessToken](../../atl/reference/caccesstoken-class.md)의 주소 이거나, 연결이 존재 하지 않는 경우 NULL입니다.

### <a name="remarks"></a>설명

**Detach** 를 호출 하면 `CAutoRevertImpersonation` 개체가 현재이 개체와 연결 된 [CAccessToken](../../atl/reference/caccesstoken-class.md) 개체에 현재 적용 되 고 있는 모든 가장을 되돌리지 않습니다. `CAutoRevertImpersonation`은 그런 다음 다시 [연결](#attach) 사용하여 동일한 또는 다른 `CAccessToken` 개체에 영향을 주지않고 소멸시킬 수 있습니다.

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a> CAutoRevertImpersonation:: GetAccessToken

이 개체와 연결 된 현재 액세스 토큰을 검색 합니다.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>반환 값

이전에 연결 된 [CAccessToken](../../atl/reference/caccesstoken-class.md)의 주소 이거나, 연결이 존재 하지 않는 경우 NULL입니다.

### <a name="remarks"></a>설명

개체의 가장 변경할지를 포함 하는 목적에 대해이 메서드를 호출 하는 경우에는 `CAccessToken` [Detach](#detach) 메서드를 대신 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[보안 되지 않은 보안 샘플](../../overview/visual-cpp-samples.md)<br/>
[액세스 토큰](/windows/win32/SecAuthZ/access-tokens)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
