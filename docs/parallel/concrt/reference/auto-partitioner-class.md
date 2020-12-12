---
description: Auto_partitioner 클래스에 대해 자세히 알아보세요.
title: auto_partitioner 클래스
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: d8e099c7a3132ce89f81df65d7e18a5c6c673697
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172260"
---
# <a name="auto_partitioner-class"></a>auto_partitioner 클래스

`auto_partitioner` 클래스는 `parallel_for`, `parallel_for_each` 및 `parallel_transform`이 반복하는 범위를 분할하는 데 사용하는 기본 방법을 나타냅니다. 이 분할 방법은 부하 분산 및 반복 별 취소에 대해 범위 가로채기를 채택 합니다.

## <a name="syntax"></a>구문

```cpp
class auto_partitioner;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[auto_partitioner](#ctor)|`auto_partitioner` 개체를 생성합니다.|
|[~ auto_partitioner 소멸자](#dtor)|`auto_partitioner` 개체를 제거합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`auto_partitioner`

## <a name="requirements"></a>요구 사항

**헤더:** ppl. h

**네임 스페이스:** 동시성

## <a name="auto_partitioner"></a><a name="dtor"></a> ~ auto_partitioner

`auto_partitioner` 개체를 제거합니다.

```cpp
~auto_partitioner();
```

## <a name="auto_partitioner"></a><a name="ctor"></a> auto_partitioner

`auto_partitioner` 개체를 생성합니다.

```cpp
auto_partitioner();
```

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
