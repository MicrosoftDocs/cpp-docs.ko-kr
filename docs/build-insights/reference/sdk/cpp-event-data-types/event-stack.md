---
title: EventStack 클래스
description: C++ Build Insights SDK EventStack 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b4f1e92011acdf8272fe631843c03c2f960a1234
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920712"
---
# <a name="eventstack-class"></a>EventStack 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`EventStack` 클래스는 [Event](event.md) 개체 컬렉션입니다. Build Insights SDK에서 받은 모든 이벤트는 C++ `EventStack` 개체 형식으로 제공됩니다. 이 스택의 마지막 항목은 현재 처리 중인 이벤트입니다. 마지막 항목 앞에 오는 항목은 현재 이벤트의 부모 계층입니다. C++ Build Insights에서 사용하는 이벤트 모델에 대한 자세한 내용은 [이벤트 테이블](../event-table.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

[EventStack](#event-stack)

### <a name="functions"></a>Functions

[Back](#back)
[operator[]](#subscript-operator)
[Size](#size)

## <a name="back"></a><a name="back"></a> Back

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>반환 값

스택의 마지막 항목을 나타내는 [RawEvent](raw-event.md) 개체입니다. 이벤트 스택의 마지막 항목은 트리거된 이벤트입니다.

## <a name="eventstack"></a><a name="event-stack"></a> EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>매개 변수

*data*\
`EventStack`이 빌드되는 원시 데이터입니다.

### <a name="remarks"></a>설명

`EventStack` 개체는 대부분 직접 생성하지 않아도 됩니다. 분석 또는 다시 로깅 세션 중에 이벤트가 처리되면 C++ Build Insights SDK에서 이 개체를 제공합니다.

## <a name="operator"></a><a name="subscript-operator"></a> operator[]

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>매개 변수

*index*\
이벤트 스택의 액세스에 대한 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

이벤트 스택의 *index* 로 표시하는 위치에 저장된 이벤트를 나타내는 [RawEvent](raw-event.md) 개체입니다.

## <a name="size"></a><a name="size"></a> 크기

```cpp
size_t Size() const;
```

### <a name="return-value"></a>반환 값

이벤트 스택의 크기입니다.

::: moniker-end
