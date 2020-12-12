---
description: Bad_function_call 클래스에 대해 자세히 알아보세요.
title: bad_function_call 클래스
ms.date: 11/04/2016
f1_keywords:
- functional/std::bad_function_call
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
ms.openlocfilehash: 659630874f84ea9e7d164b560408b162f07e1f68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321601"
---
# <a name="bad_function_call-class"></a>bad_function_call 클래스

잘못된 함수 호출을 보고합니다.

## <a name="syntax"></a>구문

```cpp
class bad_function_call : public std::exception {};
```

## <a name="remarks"></a>설명

이 클래스는 [function 클래스](../standard-library/function-class.md)에서 `operator()`에 대한 호출이 있었음을 나타내기 위해 throw된 예외를 설명합니다.
