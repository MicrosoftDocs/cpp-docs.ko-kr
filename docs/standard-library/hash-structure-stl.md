---
description: '자세히 알아보기: hash Structure (c + + 표준 라이브러리)'
title: hash 구조체(C++ 표준 라이브러리)| Microsoft 문서
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: 095566b6855c837c3ee6049a5cbedfbb087420bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324070"
---
# <a name="hash-structure-c-standard-library"></a>hash 구조체(C++ 표준 라이브러리)

`Val`에 의해 고유하게 결정되는 값을 반환하는 멤버 함수를 정의합니다. 멤버 함수는 `thread::id` 형식의 값을 인덱스 값의 분포에 매핑하는 데 적합한 [hash](../standard-library/hash-class.md) 함수를 정의합니다.

## <a name="syntax"></a>Syntax

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>요구 사항

**헤더:**\<thread>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<thread>](../standard-library/thread.md)\
[unary_function 구조체](../standard-library/unary-function-struct.md)
