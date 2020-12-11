---
description: '자세히 알아보기: IWorkerThreadClient 인터페이스'
title: IWorkerThreadClient 인터페이스
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: fb9113c9380453dad9f647fa2f5a2095ff12cea7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157986"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 인터페이스

`IWorkerThreadClient` 는 [Cworkerthread](../../atl/reference/cworkerthread-class.md) 클래스의 클라이언트에서 구현 하는 인터페이스입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
__interface IWorkerThreadClient
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[CloseHandle](#closehandle)|이 개체와 연결 된 핸들을 닫으려면이 메서드를 구현 합니다.|
|[실행](#execute)|이 개체와 연결 된 핸들이 신호를 받을 때 코드를 실행 하려면이 메서드를 구현 합니다.|

## <a name="remarks"></a>설명

신호를 받는 핸들에 대 한 응답으로 작업자 스레드에서 실행 되어야 하는 코드가 있는 경우이 인터페이스를 구현 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a> IWorkerThreadClient:: CloseHandle

이 개체와 연결 된 핸들을 닫으려면이 메서드를 구현 합니다.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>매개 변수

*hHandle*<br/>
닫을 핸들입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 반환 하거나 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드에 전달 된 핸들은 이전에 [C이상 스레드:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)을 호출 하 여이 개체와 연결 되었습니다.

### <a name="example"></a>예제

다음 코드에서는의 간단한 구현을 보여 줍니다 `IWorkerThreadClient::CloseHandle` .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a> IWorkerThreadClient:: Execute

이 개체와 연결 된 핸들이 신호를 받을 때 코드를 실행 하려면이 메서드를 구현 합니다.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>매개 변수

*dwParam*<br/>
사용자 매개 변수입니다.

*hObject*<br/>
신호를 받은 핸들입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 반환 하거나 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드에 전달 된 핸들 및 DWORD/포인터는 이전에 [C이상 thread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)을 호출 하 여이 개체와 연결 되었습니다.

### <a name="example"></a>예제

다음 코드에서는의 간단한 구현을 보여 줍니다 `IWorkerThreadClient::Execute` .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>참고 항목

[클래스](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread 클래스](../../atl/reference/cworkerthread-class.md)
