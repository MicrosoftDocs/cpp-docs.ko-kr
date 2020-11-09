---
title: EventGroup 클래스
description: C++ Build Insights SDK EventGroup 클래스 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 57cbc7a053132909149aee182b9560e2ee33c161
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923310"
---
# <a name="eventgroup-class"></a>EventGroup 클래스

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`EventGroup` 클래스 템플릿은 모든 그룹 캡처 클래스의 기본 클래스입니다.

## <a name="syntax"></a>구문

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>매개 변수

*TActivity* 그룹에 포함된 작업 형식입니다.

## <a name="members"></a>멤버

### <a name="functions"></a>Functions

[Back](#back)
[begin](#begin)
[end](#end)
[Front](#front)
[operator[]](#subscript-operator)
[Size](#size)

## <a name="back"></a><a name="back"></a> Back

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>반환 값

그룹 내 마지막 작업 이벤트에 대한 참조입니다.

## <a name="begin"></a><a name="begin"></a> begin

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>반환 값

작업 이벤트 그룹의 시작 부분을 가리키는 반복기입니다.

## <a name="end"></a><a name="end"></a> end

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>반환 값

작업 이벤트 그룹의 종료 지점 이후를 가리키는 반복기입니다.

## <a name="front"></a><a name="front"></a> Front

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>반환 값

그룹의 첫 번째 작업 이벤트에 대한 참조입니다.

## <a name="operator"></a><a name="subscript-operator"></a> operator[]

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>매개 변수

*index*\
작업 이벤트 그룹의 액세스에 대한 요소의 인덱스입니다.

### <a name="return-value"></a>반환 값

*index* 로 표시하는 위치에 저장된 이벤트 스택의 이벤트입니다.

## <a name="size"></a><a name="size"></a> 크기

```cpp
size_t Size() const;
```

### <a name="return-value"></a>반환 값

이벤트 그룹의 크기입니다.

::: moniker-end
