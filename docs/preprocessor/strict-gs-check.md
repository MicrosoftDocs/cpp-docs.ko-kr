---
description: '다음에 대 한 자세한 정보: strict_gs_check pragma'
title: strict_gs_check pragma
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 3fa1600bba59077ff66bfb0184bdd3ca4fe0e326
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197311"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check pragma

이 pragma는 향상된 보안 검사를 제공합니다.

## <a name="syntax"></a>Syntax

> **#pragma strict_gs_check (** [ **push,** ] { **on**  |  **off** } **)**\
> **pop (#pragma strict_gs_check)**

## <a name="remarks"></a>설명

스택 기반 버퍼 오버런의 일부 범주를 감지하는 데 도움이 되는 임의의 쿠키를 함수 스택에 삽입하도록 컴파일러에 지시합니다. 기본적으로 `/GS` (Buffer Security Check) 컴파일러 옵션은 모든 함수에 대해 쿠키를 삽입 하지 않습니다. 자세한 내용은 [/gs (버퍼 보안 검사)](../build/reference/gs-buffer-security-check.md)를 참조 하세요.

를 사용 하 여 `/GS` **strict_gs_check** 사용 하도록 설정 합니다.

잠재적으로 유해한 데이터에 노출되는 코드 모듈에서 이 pragma를 사용합니다. **strict_gs_check** 은 적극적인 pragma 이며이 방어가 필요 하지 않을 수 있는 함수에 적용 되지만, 결과 응용 프로그램의 성능에 미치는 영향을 최소화 하도록 최적화 됩니다.

이 pragma를 사용하는 경우에도 안전한 코드를 작성하기 위해 노력해야 합니다. 즉, 코드에 버퍼 오버런이 없는지 확인 합니다. **strict_gs_check** 코드에 남아 있는 버퍼 오버런 으로부터 응용 프로그램을 보호할 수 있습니다.

## <a name="example"></a>예제

이 샘플에서는 배열을 로컬 배열에 복사할 때 버퍼 오버런이 발생 합니다. 를 사용 하 여이 코드 `/GS` 를 컴파일하면 배열 데이터 형식이 포인터 이므로 스택에 쿠키가 삽입 되지 않습니다. **Strict_gs_check** pragma를 추가 하면 스택 쿠키가 함수 스택에 강제로 적용 됩니다.

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // **_ This buffer is subject to being overrun!! _*_
    void _pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS(버퍼 보안 검사)](../build/reference/gs-buffer-security-check.md)
