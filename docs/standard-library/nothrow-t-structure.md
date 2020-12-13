---
description: '다음에 대 한 자세한 정보: nothrow_t 구조체'
title: nothrow_t 구조체
ms.date: 11/04/2016
f1_keywords:
- nothrow_t
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
ms.openlocfilehash: 974fbe3a1e27da41c6366c62d748426293a54437
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338092"
---
# <a name="nothrow_t-structure"></a>nothrow_t 구조체

이 구조체는 함수가 예외를 발생시키는 대신 null 포인터를 반환하여 할당 오류를 보고해야 함을 나타내기 위해 new 연산자에 대한 함수 매개 변수로 사용됩니다.

## <a name="syntax"></a>구문

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>설명

컴파일러는 이 구조체를 통해 올바른 생성자 버전을 선택할 수 있습니다. [nothrow](../standard-library/new-functions.md#nothrow)는 `std::nothrow_t` 형식의 개체와 동일한 의미입니다.

## <a name="example"></a>예제

`std::nothrow_t`를 함수 매개 변수로 사용하는 방법의 예제는 [operator new](../standard-library/new-operators.md#op_new) 및 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)를 참조하세요.
