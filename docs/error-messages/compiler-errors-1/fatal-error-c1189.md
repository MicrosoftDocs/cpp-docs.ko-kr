---
description: '자세한 정보: 심각한 오류 C1189'
title: 심각한 오류 C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 4e71903c6567aedf85de81db59b66e45684d8507
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123593"
---
# <a name="fatal-error-c1189"></a>심각한 오류 C1189

> **\# 오류:** *사용자가 제공한 오류 메시지*

## <a name="remarks"></a>설명

C1189는 지시문에 의해 생성 됩니다 `#error` . 지시문을 코딩 하는 개발자는 오류 메시지의 텍스트를 지정 합니다. 자세한 내용은 [#error 지시문 (C/c + +)](../../preprocessor/hash-error-directive-c-cpp.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C1189를 생성 합니다. 이 샘플에서는 `_WIN32` 식별자가 정의 되지 않았기 때문에 개발자가 사용자 지정 오류 메시지를 발행 합니다.

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>참고 항목

[#define 지시문 (C/c + +)](../../preprocessor/hash-define-directive-c-cpp.md)
