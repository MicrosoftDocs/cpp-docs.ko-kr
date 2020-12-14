---
description: '자세히 알아보기: STACKSIZE'
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: b5d52bccc09979084b9023d380e86fe90e4def32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230343"
---
# <a name="stacksize"></a>STACKSIZE

스택 크기를 바이트 단위로 설정합니다.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>설명

스택을 설정 하는 동일한 방법은 [Stack 할당](stack-stack-allocations.md) (/STACK) 옵션을 사용 하는 것입니다. *예약* 및 인수에 대 한 자세한 내용은 해당 옵션에 대 한 설명서를 참조 하세요 `commit` .

이 옵션은 Dll에는 영향을 주지 않습니다.

## <a name="see-also"></a>참고 항목

[Module-Definition 문에 대 한 규칙](rules-for-module-definition-statements.md)
