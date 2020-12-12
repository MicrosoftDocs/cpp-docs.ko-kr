---
description: '자세한 정보: c + + 라이브러리 내부에 대 한 종속성 수정'
title: C + + 라이브러리 내부에 대 한 종속성 수정
ms.date: 05/24/2017
helpviewer_keywords:
- library internals in an upgraded Visual Studio C++ project
- _Hash_seq in an upgraded Visual Studio C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
ms.openlocfilehash: 5d9cbcdd039786c3f1bb637e6a59bcfce43bc883
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341544"
---
# <a name="fix-your-dependencies-on-c-library-internals"></a>C + + 라이브러리 내부에 대 한 종속성 수정

Microsoft는 표준 라이브러리, 대부분의 C 런타임 라이브러리, 기타 여러 Visual Studio 버전의 Microsoft 라이브러리에 대한 소스 코드를 게시했습니다. 소스 코드를 게시한 이유는 라이브러리 동작을 이해하고 코드를 디버그하는 데 도움을 주기 위해서입니다. 라이브러리 소스 코드 게시의 한 가지 부작용은 라이브러리 인터페이스의 일부가 아닌 내부 값, 데이터 구조 및 함수가 노출된다는 점입니다. 여기에는 일반적으로 두 개의 밑줄 또는 한 개의 밑줄 뒤에 한 개의 대문자로 시작되는 이름이 있습니다. 이것은 C++ 표준이 구현을 위해 예약하는 이름입니다. 이러한 값, 구조 및 함수는 시간이 지나면서 라이브러리가 진화함에 따라 달라질 수 있는 구현 세부 사항이므로 여기에 지나치게 의존하지 않는 것이 좋습니다. 여기에 의존하는 경우에는 새 라이브러리 버전으로 코드를 마이그레이션할 때 문제가 생기거나 코드를 이동하지 못하게 될 위험이 있습니다.

대부분의 경우에는 Visual Studio의 각 릴리스에 대한 새로운 기능 또는 변경 내용 문서에서 라이브러리 내부 요소에 대한 변경 사항을 언급하지 않습니다. 따라서 이러한 구현 정보에 의해 영향을 받지 않아야 합니다. 그러나 때로는 라이브러리 내부에서 볼 수 있는 일부 코드를 사용하고 싶을 때가 있을 것입니다. 이 항목에서는 사용할 수 있는 CRT 또는 표준 라이브러리 내부 요소에 대한 종속성 및 코드를 업데이트하여 이러한 종속성을 제거함으로써 이동성을 높이거나 새 라이브러리 버전으로 마이그레이션하는 방법에 관해 설명합니다.

## <a name="_hash_seq"></a>_Hash_seq

표준 라이브러리의 최신 버전에서는 일부 문자열 형식에 대해 `std::hash`를 구현하는 데 사용되는 내부 해시 함수 `std::_Hash_seq(const unsigned char *, size_t)`가 표시되었습니다. 이 함수는 문자 시퀀스에 대해 [FNV-1a 해시]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function)를 구현했습니다.

이 종속성을 제거하는 방법은 두 가지입니다.

- `basic_string`과 동일한 해시 코드 기계를 사용하여 순서가 지정되지 않은 컨테이너에 `const char *` 시퀀스를 설정하려면 `std::string_view`를 이용하는 `std::hash` 템플릿 오버로드를 사용하여 이동 가능한 방법으로 해당 해시 태그를 반환하면 됩니다. 문자열 라이브러리 코드는 향후 FNV-1a 해시 사용에 의존할 수도 있고 아닐 수도 있으므로 특정 해시 알고리즘에 대한 종속성을 피하는 것이 가장 좋은 방법입니다.

- 임의의 메모리에 대해 FNV-1a 해시를 생성하려는 사용자를 위해 [MIT 라이선스](https://github.com/Microsoft/VCSamples/blob/master/license.txt)에 따라 독립 실행형 헤더 파일 [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq)의 [VCSamples]( https://github.com/Microsoft/vcsamples) 리포지토리에 있는 GitHub에서 이 코드를 사용할 수 있도록 만들었습니다. 사용자 편의를 위해 여기에도 복사본을 넣었습니다. 이 코드를 헤더 파일에 복사하고 영향을 받는 모든 코드에 헤더를 추가한 다음 `_Hash_seq`를 찾아 `fnv1a_hash_bytes`로 바꿀 수 있습니다. 동일한 동작을 `_Hash_seq`에서 내부 구현으로 가져오게 됩니다.

```cpp
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved.
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;
#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
    {
        // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
    }
    return (result);
}
```

## <a name="see-also"></a>참고 항목

[이전 버전의 Visual C++에서 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[잠재적인 업그레이드 문제 개요(Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[코드를 유니버설 CRT로 업그레이드](upgrade-your-code-to-the-universal-crt.md)
