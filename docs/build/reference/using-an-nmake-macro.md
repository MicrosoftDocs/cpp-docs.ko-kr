---
description: '자세한 정보: NMAKE 매크로 사용'
title: NMAKE 매크로 사용
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: 14a1856b411bf7608b94caacb1b0b078dd1f5577
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247009"
---
# <a name="using-an-nmake-macro"></a>NMAKE 매크로 사용

매크로를 사용 하려면 다음과 같이 이름 앞에 달러 기호 ($)를 사용 하 여 해당 이름을 괄호로 묶습니다.

## <a name="syntax"></a>구문

```
$(macroname)
```

## <a name="remarks"></a>설명

공백은 허용 되지 않습니다. *Macroname* 이 단일 문자인 경우 괄호는 선택 사항입니다. 정의 문자열은 $ (*macroname*)로 바뀝니다. 정의 되지 않은 매크로는 null 문자열로 바뀝니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

[매크로 대체](macro-substitution.md)

## <a name="see-also"></a>참고 항목

[매크로와 NMake](macros-and-nmake.md)
