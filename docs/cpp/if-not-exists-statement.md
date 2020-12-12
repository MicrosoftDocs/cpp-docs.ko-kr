---
description: '다음에 대 한 자세한 정보: __if_not_exists 문'
title: __if_not_exists 문
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 29f98c2d07858077207c10dfcdd45b9ce51268e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113950"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists 문

**`__if_not_exists`** 문은 지정 된 식별자가 있는지 여부를 테스트 합니다. 식별자가 없는 경우 지정된 문 블록이 실행됩니다.

## <a name="syntax"></a>구문

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>매개 변수

*identifier*\
존재 여부를 테스트할 식별자입니다.

*할당문*\
*식별자* 가 없는 경우 실행할 하나 이상의 문입니다.

## <a name="remarks"></a>설명

> [!CAUTION]
> 가장 안정적인 결과를 얻으려면 **`__if_not_exists`** 다음 제약 조건에서 문을 사용 합니다.

- **`__if_not_exists`** 문은 템플릿이 아닌 단순 형식에만 적용 합니다.

- **`__if_not_exists`** 클래스 내부 또는 외부의 식별자에 문을 적용 합니다. **`__if_not_exists`** 문을 지역 변수에 적용 하지 마십시오.

- **`__if_not_exists`** 문은 함수 본문 에서만 사용 합니다. 함수 본문 외부에서 **`__if_not_exists`** 문은 완전히 정의 된 형식만 테스트할 수 있습니다.

- 오버로드된 함수에 대해 테스트할 때 특정 양식의 오버로드를 테스트할 수 없습니다.

문에 대 한 보수는 **`__if_not_exists`** [__if_exists](../cpp/if-exists-statement.md) 문입니다.

## <a name="example"></a>예제

를 사용 하는 방법에 대 한 예제는 **`__if_not_exists`** [__if_exists 문](../cpp/if-exists-statement.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[선택문](../cpp/selection-statements-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[__if_exists 문](../cpp/if-exists-statement.md)
