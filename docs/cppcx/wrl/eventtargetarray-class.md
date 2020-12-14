---
description: '자세한 정보: EventTargetArray 클래스'
title: EventTargetArray 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: ac3199d2374a47e94705f8f51672bfedd0b7bf20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198585"
---
# <a name="eventtargetarray-class"></a>EventTargetArray 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>설명

이벤트 처리기의 배열을 나타냅니다.

[EventSource](eventsource-class.md) 개체와 연결 된 이벤트 처리기는 보호 된 데이터 멤버에 저장 됩니다 `EventTargetArray` .

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                           | 설명
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray:: EventTargetArray](#eventtargetarray)        | `EventTargetArray` 클래스의 새 인스턴스를 초기화합니다.
[EventTargetArray:: ~ EventTargetArray](#tilde-eventtargetarray) | 현재 클래스를 초기화 `EventTargetArray` 합니다.

### <a name="public-methods"></a>Public 메서드

이름                                  | 설명
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray:: AddTail](#addtail) | 지정 된 이벤트 처리기를 이벤트 처리기의 내부 배열 끝에 추가 합니다.
[EventTargetArray:: Begin](#begin)     | 이벤트 처리기의 내부 배열에서 첫 번째 요소의 주소를 가져옵니다.
[EventTargetArray:: End](#end)         | 이벤트 처리기의 내부 배열에서 마지막 요소의 주소를 가져옵니다.
[EventTargetArray:: Length](#length)   | 이벤트 처리기의 내부 배열에 있는 현재 요소 수를 가져옵니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`EventTargetArray`

## <a name="requirements"></a>요구 사항

**헤더:** 이벤트. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a> EventTargetArray:: ~ EventTargetArray

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>설명

현재 클래스를 초기화 `EventTargetArray` 합니다.

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a> EventTargetArray:: AddTail

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>매개 변수

*요소인*<br/>
추가할 이벤트 처리기에 대 한 포인터입니다.

### <a name="remarks"></a>설명

지정 된 이벤트 처리기를 이벤트 처리기의 내부 배열 끝에 추가 합니다.

`AddTail()` 는 클래스 에서만 내부적으로 사용 됩니다 `EventSource` .

## <a name="eventtargetarraybegin"></a><a name="begin"></a> EventTargetArray:: Begin

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>반환 값

이벤트 처리기의 내부 배열에 있는 첫 번째 요소의 주소입니다.

### <a name="remarks"></a>설명

이벤트 처리기의 내부 배열에서 첫 번째 요소의 주소를 가져옵니다.

## <a name="eventtargetarrayend"></a><a name="end"></a> EventTargetArray:: End

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>반환 값

이벤트 처리기의 내부 배열에서 마지막 요소의 주소입니다.

### <a name="remarks"></a>설명

이벤트 처리기의 내부 배열에서 마지막 요소의 주소를 가져옵니다.

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a> EventTargetArray:: EventTargetArray

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>매개 변수

*시간*<br/>
이 생성자 작업 후에 *hr* 매개 변수는 배열 할당이 성공 했는지 아니면 실패 했는지를 나타냅니다. 다음 목록에서는 *hr* 에 사용할 수 있는 값을 보여 줍니다.

- S_OK<br/>
  작업에 성공했습니다.

- E_OUTOFMEMORY<br/>
  배열에 대해 메모리를 할당할 수 없습니다.

- S_FALSE<br/>
  매개 변수 *항목이* 0 보다 작거나 같습니다.

*items*<br/>
할당할 배열 요소의 수입니다.

### <a name="remarks"></a>설명

`EventTargetArray` 클래스의 새 인스턴스를 초기화합니다.

`EventTargetArray` 는 이벤트 처리기의 배열을 개체에 보관 하는 데 사용 됩니다 `EventSource` .

## <a name="eventtargetarraylength"></a><a name="length"></a> EventTargetArray:: Length

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
size_t Length();
```

### <a name="return-value"></a>반환 값

이벤트 처리기의 내부 배열에 있는 현재 요소 수입니다.

### <a name="remarks"></a>설명

이벤트 처리기의 내부 배열에 있는 현재 요소 수를 가져옵니다.
