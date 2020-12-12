---
description: Is_trivially_copyable 클래스에 대해 자세히 알아보세요.
title: is_trivially_copyable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: 0c3590f1549f064492b361ae2ddeff665e9365ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118474"
---
# <a name="is_trivially_copyable-class"></a>is_trivially_copyable 클래스

형식이 일반적으로 복사 가능한 형식인지를 테스트합니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>매개 변수

*트*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 조건자의 인스턴스는 *T* 형식이 일반적으로 복사할 수 있는 형식인 경우 true이 고 그렇지 않은 경우 false입니다. 일반적으로 복사 가능한 형식에는 특수한 복사 작업, 이동 작업 또는 소멸자가 없습니다. 일반적으로 복사 작업은 비트 복사로 구현할 수 있는 경우 trivial로 간주됩니다. 기본 제공 형식과 일반적으로 복사 가능한 형식의 배열은 모두 일반적으로 복사 가능합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
