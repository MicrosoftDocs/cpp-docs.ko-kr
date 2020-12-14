---
description: Simple_partitioner 클래스에 대해 자세히 알아보세요.
title: simple_partitioner 클래스
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 76dcac6d7fc2dce5b69d0a9dbefaf01420f8bcde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188692"
---
# <a name="simple_partitioner-class"></a>simple_partitioner 클래스

`simple_partitioner` 클래스는 `parallel_for`에서 반복하는 범위의 정적 분할을 나타냅니다. 파티셔너는 각 청크에 적어도 청크 크기로 지정된 개수의 반복이 있도록 범위를 청크로 나눕니다.

## <a name="syntax"></a>구문

```cpp
class simple_partitioner;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[simple_partitioner](#ctor)|`simple_partitioner` 개체를 생성합니다.|
|[~ simple_partitioner 소멸자](#dtor)|`simple_partitioner` 개체를 제거합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`simple_partitioner`

## <a name="requirements"></a>요구 사항

**헤더:** ppl. h

**네임 스페이스:** 동시성

## <a name="simple_partitioner"></a><a name="dtor"></a> ~ simple_partitioner

`simple_partitioner` 개체를 제거합니다.

```cpp
~simple_partitioner();
```

## <a name="simple_partitioner"></a><a name="ctor"></a> simple_partitioner

`simple_partitioner` 개체를 생성합니다.

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>매개 변수

*_Chunk_size*<br/>
최소 파티션 크기입니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
