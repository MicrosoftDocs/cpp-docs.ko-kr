---
title: AgileEventSource 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f2ee187087917220751155cc43e8619e6dcf763
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054576"
---
# <a name="agileeventsource-class"></a>AgileEventSource 클래스

모든 스레드에서 액세스할 수 있는 구성 요소는 agile 구성 요소에서 발생 하는 이벤트를 나타냅니다. 상속 [EventSource](eventsource-class.md) 재정의 `Add` agile 이벤트를 호출 하는 방법에 대 한 옵션을 지정 하는 추가 형식 매개 변수를 사용 하 여 멤버 함수입니다.

## <a name="syntax"></a>구문

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>매개 변수

*TDelegateInterface*<br/>
인터페이스 이벤트 처리기를 나타내는 대리자입니다.

*TEventSourceOptions*<br/>
[InvokeModeOptions](invokemodeoptions-structure.md) invokeMode 필드를로 갖는 `InvokeMode::StopOnFirstError` 또는 `InvokeMode::FireAll`합니다.

## <a name="remarks"></a>설명

대부분의 Windows 런타임 구성 요소는 agile 구성 요소입니다. 자세한 내용은 [스레딩 및 마샬링 (C + + /cli CX)](../cppcx/threading-and-marshaling-c-cx.md)합니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>요구 사항

**헤더:** event.h

**네임스페이스:** Microsoft::WRL

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[AgileEventSource::Add 메서드](#add)|현재 이벤트 처리기 집합에 지정 된 대리자를 인터페이스에 의해 표시 agile 이벤트 처리기 추가 **AgileEventSource** 개체입니다.|

## <a name="add"></a> AgileEventSource::Add 메서드

현재 이벤트 처리기 집합에 지정 된 대리자를 인터페이스에 의해 표시 되는 이벤트 처리기 추가 [EventSource](eventsource-class.md) 개체입니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>매개 변수

*delegateInterface*<br/>
이벤트 처리기를 나타내는 대리자 개체에 대 한 인터페이스입니다.

*token*<br/>
이 작업이 완료 될 때 이벤트를 나타내는 핸들입니다. 이 토큰을 사용 하 여 매개 변수로 `Remove()` 이벤트 처리기를 삭제 하는 방법입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="see-also"></a>참고 항목

[Microsoft::WRL 네임스페이스](../windows/microsoft-wrl-namespace.md)