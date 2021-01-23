---
description: pragmaMicrosoft C/c + +의 auto_inline 지시문에 대해 자세히 알아보세요.
title: auto_inline pragma
ms.date: 01/22/2021
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragma, auto_inline
- auto_inline pragma
no-loc:
- pragma
ms.openlocfilehash: 72c6823acf260d48883142f8568483eb78155da1
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713729"
---
# <a name="auto_inline-no-locpragma"></a>`auto_inline` pragma

**`off`** 자동 인라인 확장의 후보로 고려 되지 않도록 지정 된 범위 내에서 정의 된 모든 함수를 제외 합니다.

## <a name="syntax"></a>구문

> **`#pragma auto_inline(`** [ { **`on`** | **`off`** } ] **`)`**

## <a name="remarks"></a>설명

를 사용 하려면 **`auto_inline`** pragma 함수 정의 앞과 뒤에를 추가 합니다. 는 pragma 의 첫 번째 함수 정의가 표시 되는 즉시 적용 됩니다 pragma .

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
