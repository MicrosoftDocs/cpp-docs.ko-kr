---
title: Swap 함수 (Windows Runtime c + + 템플릿 라이브러리) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
dev_langs:
- C++
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b5273127b4f4329427f50c82f1bb15a4ad2634e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590211"
---
# <a name="swap-function-windows-runtime-c-template-library"></a>Swap 함수(Windows Runtime C++ 템플릿 라이브러리)

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>매개 변수

*left*  
첫 번째 인수입니다.

*right*  
두 번째 인수입니다.

## <a name="return-value"></a>반환 값

## <a name="remarks"></a>설명

두 개의 지정 된 인수 값을 교환 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Details 네임스페이스](../windows/microsoft-wrl-details-namespace.md)