---
title: hash 구조체(C++ 표준 라이브러리)| Microsoft 문서
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: bb230d401d5061f4951f8007f93c3a28ce3dab03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579866"
---
# <a name="hash-structure-c-standard-library"></a>hash 구조체(C++ 표준 라이브러리)

`Val`에 의해 고유하게 결정되는 값을 반환하는 멤버 함수를 정의합니다. 멤버 함수는 `thread::id` 형식의 값을 인덱스 값의 분포에 매핑하는 데 적합한 [hash](../standard-library/hash-class.md) 함수를 정의합니다.

## <a name="syntax"></a>구문

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>요구 사항

**헤더:** \<스레드 >

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<thread>](../standard-library/thread.md)<br/>
[unary_function 클래스](../standard-library/unary-function-struct.md)<br/>
