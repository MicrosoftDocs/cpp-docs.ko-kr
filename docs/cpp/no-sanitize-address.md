---
description: '다음에 대 한 자세한 정보: no_sanitize_address'
title: no_sanitize_address
ms.date: 11/04/2016
f1_keywords:
- no_sanitize_address__cpp
helpviewer_keywords:
- __declspec keyword [C++], no_sanitize_address
- no_sanitize_address __declspec keyword
ms.openlocfilehash: a18b60f666bc53ef72db3a6d230dc7531cc6bc1f
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471197"
---
# `no_sanitize_address`

**Microsoft 전용**

**`__declspec(no_sanitize_address)`** 지정자는 함수, 지역 변수 또는 전역 변수에 대해 sanitizer 주소를 사용 하지 않도록 컴파일러에 지시 합니다. 이 지정자는 [AddressSanitizer](../sanitizers/asan.md)와 함께 사용 됩니다.

> [!NOTE]
> **`__declspec(no_sanitize_address)`***런타임* 동작이 아닌 _컴파일러_ 동작을 사용 하지 않도록 설정 합니다.

## <a name="example"></a>예제

예제는 [AddressSanitizer build 참조](../sanitizers/asan-building.md#__declspecno_sanitize_address) 를 참조 하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`__declspec`](../cpp/declspec.md)\
[어](../cpp/keywords-cpp.md)\
[AddressSanitizer](../sanitizers/asan.md)
