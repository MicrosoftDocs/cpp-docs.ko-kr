---
description: Ctype_base 클래스에 대해 자세히 알아보세요.
title: ctype_base 클래스
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 430e6fbf77842e61e662fd3024a54b418f487748
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324684"
---
# <a name="ctype_base-class"></a>ctype_base 클래스

클래스는 클래스 템플릿 [ctype](../standard-library/ctype-class.md)의 패싯에 대 한 기본 클래스로 사용 됩니다. 개별적으로 또는 전체 범위 내에서 특성을 분류 또는 테스트하는 데 사용하는 열거형을 정의하는 데 사용하는 ctype 클래스의 기본 클래스입니다.

## <a name="syntax"></a>구문

```cpp
struct ctype_base : public locale::facet
{
    enum
    {
        alnum,
        alpha,
        cntrl,
        digit,
        graph,
        lower,
        print,
        punct,
        space,
        upper,
        xdigit
    };
    typedef short mask;

    ctype_base( size_t _Refs = 0 );
    ~ctype_base();
};
```

## <a name="remarks"></a>설명

열거형 마스크를 정의합니다. 각 열거형 상수는 헤더에 선언 된 유사한 이름을 사용 하 여 함수에 의해 정의 된 대로 문자를 분류 하는 다른 방법을 특징으로 \<ctype.h> 합니다. 상수는 다음과 같습니다.

- **space**([isspace](../standard-library/locale-functions.md#isspace) 함수)

- **print**([isprint](../standard-library/locale-functions.md#isprint) 함수)

- **cntrl**([iscntrl](../standard-library/locale-functions.md#iscntrl) 함수)

- **upper**(함수 [isupper](../standard-library/locale-functions.md#isupper))

- **lower**([islower](../standard-library/locale-functions.md#islower) 함수)

- **digit**([isdigit](../standard-library/locale-functions.md#isdigit) 함수)

- **punct**([ispunct](../standard-library/locale-functions.md#ispunct) 함수)

- **xdigit**([isxdigit](../standard-library/locale-functions.md#isxdigit) 함수)

- **alpha**([isalpha](../standard-library/locale-functions.md#isalpha) 함수)

- **alnum**([isalnum](../standard-library/locale-functions.md#isalnum) 함수)

- **graph**([isgraph](../standard-library/locale-functions.md#isgraph) 함수)

이러한 상수를 OR 연산하여 분류의 조합을 특징지을 수 있습니다. 특히 **alnum과** = = ( **alpha** &#124; **digit** \) 및 **graph** \= \= \( **alnum과** &#124; **punct**)는 항상 true입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
