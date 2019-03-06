---
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: 8669198ee62032e15e40c821ed2e4caccdebe519
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417491"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>설명

이 옵션을 라이브러리에 정의 된 공용 기호를 표시 합니다. 해당 오프셋 함께 개체 순서로 기호를 표시 하려면 1 인수를 지정 합니다. 오프셋 및 개체의 인덱스 번호를 표시 하려면 2 인수를 지정 하 고 기호 각각에 대 한 개체 인덱스와 함께 사전순으로 나열 합니다. 두 출력을 가져오려면 /LINKERMEMBER 숫자 인수 없이 지정 합니다.

[/HEADERS](../../build/reference/headers.md) DUMPBIN 옵션은 [/GL](../../build/reference/gl-whole-program-optimization.md) 컴파일러 옵션으로 만든 파일에만 사용할 수 있습니다.

## <a name="see-also"></a>참고자료

[DUMPBIN 옵션](../../build/reference/dumpbin-options.md)
