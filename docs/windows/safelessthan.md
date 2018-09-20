---
title: SafeLessThan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThan
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a5824b1e3ba050cf8c6d9c0f7b56231211f1f59a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377203"
---
# <a name="safelessthan"></a>SafeLessThan

1 개의 숫자 다른 노드보다 작은지 여부를 결정 합니다.

## <a name="syntax"></a>구문

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>매개 변수

*t*<br/>
[in] 첫 번째 숫자입니다. 이 형식 이어야 합니다 `T`합니다.

*u*<br/>
[in] 두 번째 필드가 됩니다. 이 형식 이어야 합니다 `U`합니다.

## <a name="return-value"></a>반환 값

**true** 하는 경우 *t* 는 미만 *u*이 고 그렇지 않으면 **false**합니다.

## <a name="remarks"></a>설명

이 메서드는 때문에 표준 비교 연산자를 향상 **SafeLessThan** 두 가지 유형의 수를 비교할 수 있습니다.

이 메서드는 부분 [SafeInt 라이브러리](../windows/safeint-library.md) 의 인스턴스를 만들지 않고 단일 비교 작업에 대 한 설계 되는 [SafeInt 클래스](../windows/safeint-class.md)합니다.

> [!NOTE]
> 이 메서드는 단일 수학 연산을 보호해야 하는 경우에만 사용해야 합니다. 여러 작업 인 경우 사용 해야는 `SafeInt` 개별 독립 실행형 함수를 호출 하는 것이 아니라 클래스입니다.

템플릿 형식에 대 한 자세한 `T` 하 고 `U`를 참조 하세요 [SafeInt 함수](../windows/safeint-functions.md)합니다.

## <a name="requirements"></a>요구 사항

**헤더:** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>참고 항목

[SafeInt 함수](../windows/safeint-functions.md)<br/>
[SafeInt 라이브러리](../windows/safeint-library.md)<br/>
[SafeInt 클래스](../windows/safeint-class.md)<br/>
[SafeLessThanEquals](../windows/safelessthanequals.md)<br/>
[SafeGreaterThan](../windows/safegreaterthan.md)<br/>
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)