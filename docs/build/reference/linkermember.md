---
description: 다음에 대 한 자세한 정보:/LINKERMEMBER
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: 76c842bcc2299b4245847e7d4e9a64656e88d2d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199391"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>설명

이 옵션은 라이브러리에 정의 된 공용 기호를 표시 합니다. 개체 순서에서 기호를 오프셋과 함께 표시 하려면 1 인수를 지정 합니다. 두 인수를 지정 하 여 개체의 오프셋 및 인덱스 번호를 표시 한 다음 각에 대 한 개체 인덱스와 함께 알파벳 순서로 기호를 나열 합니다. 두 출력을 모두 가져오려면 number 인수 없이/LINKERMEMBER를 지정 합니다.

[/GL](gl-whole-program-optimization.md) 컴파일러 옵션으로 생성된 파일에서는 [/HEADERS](headers.md) DUMPBIN옵션만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
