---
title: SafeMultiply | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeMultiply
dev_langs:
- C++
helpviewer_keywords:
- SafeMultiply function
ms.assetid: 81d988a5-fac7-4930-8c37-c24fa8e2c853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0eb1b8b37737d1c0c36af28da9b0c656e26de7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396749"
---
# <a name="safemultiply"></a>SafeMultiply

오버플로 으로부터 보호 하는 방식으로 두 개의 숫자를 곱합니다.

## <a name="syntax"></a>구문

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>매개 변수

*t*<br/>
[in] 곱할 첫 번째 숫자입니다. 이 형식 이어야 합니다 `T`합니다.

*u*<br/>
[in] 곱할 두 번째 숫자입니다. 이 형식 이어야 합니다 `U`합니다.

*결과*<br/>
[out] 매개 변수가 있는 **SafeMultiply** 결과 저장 합니다.

## <a name="return-value"></a>반환 값

**true** 오류가 발생 하지 않으면; **false** 오류가 발생 합니다.

## <a name="remarks"></a>설명

이 메서드는 부분 [SafeInt 라이브러리](../windows/safeint-library.md) 의 인스턴스를 만들지 않고 단일 곱하기 연산에 대 한 설계 되는 [SafeInt 클래스](../windows/safeint-class.md)합니다.

> [!NOTE]
> 이 메서드는 단일 수학 연산을 보호해야 하는 경우에만 사용해야 합니다. 작업이 여러 개 있으면 개별 독립 실행형 함수를 호출하는 대신 `SafeInt` 클래스를 사용해야 합니다.

템플릿 형식에 대 한 자세한 `T` 하 고 `U`를 참조 하세요 [SafeInt 함수](../windows/safeint-functions.md)합니다.

## <a name="requirements"></a>요구 사항

**헤더:** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>참고 항목

[SafeInt 함수](../windows/safeint-functions.md)<br/>
[SafeInt 라이브러리](../windows/safeint-library.md)<br/>
[SafeInt 클래스](../windows/safeint-class.md)<br/>
[SafeDivide](../windows/safedivide.md)