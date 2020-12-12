---
description: '자세히 알아보기: IRowsetNotifyImpl 클래스'
title: IRowsetNotifyImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
ms.openlocfilehash: e07f918d7315998f5aa0dc14dbd613520a68f134
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287049"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 클래스

알림을 처리할 수 있도록 소비자 ("싱크" 라고도 함)에 [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 을 구현 하 고 등록 합니다.

## <a name="syntax"></a>Syntax

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[OnFieldChange](#onfieldchange)|열 값에 대한 모든 변경 사항을 소비자에게 알립니다.|
|[OnRowChange](#onrowchange)|행의 첫 번째 변경 사항이나 전체 행에 영향을 주는 모든 변경 사항을 소비자에게 알립니다.|
|[OnRowsetChange](#onrowsetchange)|전체 행 집합에 영향을 주는 모든 변경 사항을 소비자에게 알립니다.|

## <a name="remarks"></a>설명

소비자에서 연결 지점 인터페이스 구현에 대 한 [알림 받기](../../data/oledb/receiving-notifications.md) 를 참조 하세요.

`IRowsetNotifyImpl``IRowsetNotify` `IRowsetNotify` [onfieldchange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [onfieldchange](/previous-versions/windows/desktop/ms722694(v=vs.85))및 [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))메서드에 대 한 빈 함수를 사용 하 여에 대 한 더미 구현을 제공 합니다. 인터페이스를 구현할 때이 클래스에서 상속 하는 경우 `IRowsetNotify` 필요한 메서드만 구현할 수 있습니다. 다른 메서드에 대 한 빈 구현도 제공 해야 합니다.

## <a name="irowsetnotifyimplonfieldchange"></a><a name="onfieldchange"></a> IRowsetNotifyImpl:: OnFieldChange

열 값에 대한 모든 변경 사항을 소비자에게 알립니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(OnFieldChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ HROW /* hRow */,
/* [in] */ DBORDINAL /* cColumns */,
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>매개 변수

매개 변수 설명은 [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

반환 값에 대 한 설명은 [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 를 참조 하십시오.

### <a name="remarks"></a>설명

이 메서드는 [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 메서드를 래핑합니다. 자세한 내용은 OLE DB 프로그래머 참조에서 해당 메서드의 설명을 참조하십시오.

## <a name="irowsetnotifyimplonrowchange"></a><a name="onrowchange"></a> IRowsetNotifyImpl:: OnRowChange

행의 첫 번째 변경 사항이나 전체 행에 영향을 주는 모든 변경 사항을 소비자에게 알립니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(OnRowChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBCOUNTITEM /* cRows */,
/* [size_is][in] */ const HROW /* rghRows*/ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>매개 변수

매개 변수 설명은 [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 를 참조 하십시오.

### <a name="return-value"></a>반환 값

반환 값에 대 한 설명은 [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 를 참조 하십시오.

### <a name="remarks"></a>설명

이 메서드는 [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 메서드를 래핑합니다. 자세한 내용은 OLE DB 프로그래머 참조에서 해당 메서드의 설명을 참조하십시오.

## <a name="irowsetnotifyimplonrowsetchange"></a><a name="onrowsetchange"></a> IRowsetNotifyImpl:: OnRowsetChange

전체 행 집합에 영향을 주는 모든 변경 사항을 소비자에게 알립니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>매개 변수

매개 변수 설명은 [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

반환 값에 대 한 설명은 [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

이 메서드는 [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 메서드를 래핑합니다. 자세한 내용은 OLE DB 프로그래머 참조에서 해당 메서드의 설명을 참조하십시오.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 
 [IRowsetNotifyCP 클래스](../../data/oledb/irowsetnotifycp-class.md)
