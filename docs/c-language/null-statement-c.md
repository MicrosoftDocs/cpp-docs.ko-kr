---
description: '자세한 정보: Null 문 (C)'
title: Null 문 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
ms.openlocfilehash: 362fc9e311d0495e0a3ab51da7a5042574859649
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243291"
---
# <a name="null-statement-c"></a>Null 문 (C)

"null 문"은 세미콜론만 포함하는 문입니다. 문이 예상되는 위치에 이러한 문이 표시될 수 있습니다. null 문을 실행할 때 아무 작업도 수행되지 않습니다. null 문을 코딩하는 올바른 방법은 다음과 같습니다.

## <a name="syntax"></a>구문

> **;**

## <a name="remarks"></a>설명

**`do`** , **`for`** , **`if`** , **`while`** 과 같은 문의 경우 실행 가능 문이 문 본문으로 나타나야 합니다. null 문은 실제 문 본문이 필요하지 않는 경우 구문 요구 사항을 충족합니다.

다른 C 문에서처럼 null 문 앞에 레이블을 포함할 수 있습니다. 복합 문의 닫는 중괄호와 같이 문이 아닌 항목에 레이블을 지정하려면 null 문의 레이블을 지정하고 항목 바로 앞에 해당 문을 삽입하여 동일한 효과를 얻습니다.

이 예제에서는 null 문을 보여 줍니다.

```C
for ( i = 0; i < 10; line[i++] = 0 )
     ;
```

이 예제에서 **`for`** 문 `line[i++] = 0`의 루프 식은 `line`의 처음 10개 요소를 0개로 초기화합니다. 추가 문이 필요하지 않으므로 문 본문이 null 문입니다.

## <a name="see-also"></a>참조

[문](../c-language/statements-c.md)
