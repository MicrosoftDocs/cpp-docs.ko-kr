---
description: Is_trivial 클래스에 대해 자세히 알아보세요.
title: is_trivial 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 56e5a3c915893b88228f4a40307d2c1e3c32555d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247659"
---
# <a name="is_trivial-class"></a>is_trivial 클래스

형식이 trivial 형식인지 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이 trivial 형식인 경우 true이 고 그렇지 않은 경우 false입니다. Trivial 형식은 스칼라 형식, 일반적으로 복사할 수 클래스 형식, 이러한 형식의 배열 및 이러한 형식의 cv 한정 버전입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
