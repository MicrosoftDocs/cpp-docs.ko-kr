---
description: '자세히 알아보기: AgileEventSource 클래스'
title: AgileEventSource 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: d2e48d59d8706eb65828bc5b77ffaf9d4158bc1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204578"
---
# <a name="agileeventsource-class"></a>AgileEventSource 클래스

모든 스레드에서 액세스할 수 있는 구성 요소인 agile 구성 요소에 의해 발생 하는 이벤트를 나타냅니다. [EventSource](eventsource-class.md) 에서 상속 되며, `Add` agile 이벤트를 호출 하는 방법에 대 한 옵션을 지정 하기 위해 추가 형식 매개 변수를 사용 하 여 멤버 함수를 재정의 합니다.

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
이벤트 처리기를 나타내는 대리자에 대 한 인터페이스입니다.

*TEventSourceOptions*<br/>
InvokeMode 필드가 or로 설정 된 [InvokeModeOptions](invokemodeoptions-structure.md) 구조체입니다 `InvokeMode::StopOnFirstError` `InvokeMode::FireAll` .

## <a name="remarks"></a>설명

Windows 런타임의 대부분 구성 요소는 agile 구성 요소입니다. 자세한 내용은 [스레딩 및 마샬링 (c + +/cx)](../../cppcx/threading-and-marshaling-c-cx.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>요구 사항

**헤더:** 이벤트. h

**네임스페이스:** Microsoft::WRL

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[AgileEventSource:: Add 메서드](#add)|지정 된 대리자 인터페이스가 나타내는 agile 이벤트 처리기를 현재 **AgileEventSource** 개체에 대 한 이벤트 처리기 집합에 추가 합니다.|

## <a name="agileeventsourceadd-method"></a><a name="add"></a> AgileEventSource:: Add 메서드

지정 된 대리자 인터페이스에서 나타내는 이벤트 처리기를 현재 [EventSource](eventsource-class.md) 개체에 대 한 이벤트 처리기 집합에 추가 합니다.

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

*토큰*<br/>
이 작업이 완료 되 면 이벤트를 나타내는 핸들입니다. 이 토큰을 메서드에 대 한 매개 변수로 사용 하 여 `Remove()` 이벤트 처리기를 삭제 합니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
