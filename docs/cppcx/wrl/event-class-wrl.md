---
description: '자세한 정보: 이벤트 클래스 (WRL)'
title: 이벤트 클래스 (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: e3a61a40d1160830df80a7e0650e60fbf803e3d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272827"
---
# <a name="event-class-wrl"></a>이벤트 클래스 (WRL)

이벤트를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                   | 설명
---------------------- | ------------------------------------------------
[Event:: Event](#event) | `Event` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-operators"></a>Public 연산자

Name                                 | 설명
------------------------------------ | ------------------------------------------------------------------------
[Event:: operator =](#operator-assign) | 지정 된 `Event` 참조를 현재 인스턴스에 할당 합니다 `Event` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`HandleT`

`Event`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="eventevent"></a><a name="event"></a> Event:: Event

`Event` 클래스의 새 인스턴스를 초기화합니다.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
이벤트에 대한 핸들. 기본적으로 *h* 는로 초기화 됩니다 **`nullptr`** .

## <a name="eventoperator"></a><a name="operator-assign"></a> Event:: operator =

지정 된 `Event` 참조를 현재 인스턴스에 할당 합니다 `Event` .

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
인스턴스에 대 한 rvalue 참조 `Event` 입니다.

### <a name="return-value"></a>반환 값

현재 인스턴스에 대 한 포인터 `Event` 입니다.
