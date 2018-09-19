---
title: SafeLessThanEquals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThanEquals function
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a291b7a2cd8c33e743a31d53c6330f67e915662a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713065"
---
# <a name="safelessthanequals"></a>SafeLessThanEquals

두 숫자를 비교합니다.

## <a name="syntax"></a>구문

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>매개 변수

*t*<br/>
[in] 비교할 첫 번째 숫자입니다. 이 형식 이어야 합니다 `T`합니다.

*u*<br/>
[in] 비교할 두 번째 숫자입니다. 이 형식 이어야 합니다 `U`합니다.

## <a name="return-value"></a>반환 값

**true 이면** 하는 경우 *t* 보다 작거나 같음 *u*이 고 그렇지 않으면 **false**합니다.

## <a name="remarks"></a>설명

**SafeLessThanEquals** 두 가지 유형의 숫자를 비교할 수 있도록 하 여 일반 비교 연산자를 확장 합니다.

이 메서드는 부분 [SafeInt 라이브러리](../windows/safeint-library.md) 의 인스턴스를 만들지 않고 단일 비교 작업에 대 한 설계 되는 [SafeInt 클래스](../windows/safeint-class.md)합니다.

> [!NOTE]
> 이 메서드는 단일 수학 연산을 보호해야 하는 경우에만 사용해야 합니다. 작업이 여러 개 있으면 개별 독립 실행형 함수를 호출하는 대신 `SafeInt` 클래스를 사용해야 합니다.

템플릿 형식에 대 한 자세한 `T` 하 고 `U`를 참조 하세요 [SafeInt 함수](../windows/safeint-functions.md)합니다.

## <a name="requirements"></a>요구 사항

**헤더:** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>참고 항목

[SafeInt 함수](../windows/safeint-functions.md)  
[SafeInt 라이브러리](../windows/safeint-library.md)  
[SafeInt 클래스](../windows/safeint-class.md)  
[SafeGreaterThan](../windows/safegreaterthan.md)  
[SafeLessThan](../windows/safelessthan.md)  
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)