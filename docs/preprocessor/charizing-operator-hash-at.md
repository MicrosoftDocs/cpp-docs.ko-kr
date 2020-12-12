---
description: '자세한 정보: Charizing 연산자 (# @)'
title: Charizing 연산자(#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: 6d04aa24c75153957bd6fd09824f4e94e36fd38f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300868"
---
# <a name="charizing-operator-"></a>Charizing 연산자(#@)

**Microsoft 전용**

charizing 연산자는 매크로의 인수에만 사용할 수 있습니다. `#@`가 매크로 정의의 정식 매개 변수 앞에 오면 실제 인수는 작은따옴표로 묶이고 매크로가 확장 될 때 문자로 처리 됩니다. 예를 들어:

```cpp
#define makechar(x)  #@x
```

위의 정의는 다음 문이

```cpp
a = makechar(b);
```

다음과 같이 확장되게 합니다.

```cpp
a = 'b';
```

작은따옴표 문자 ( `'` )는 charizing 연산자와 함께 사용할 수 없습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[전처리기 연산자](../preprocessor/preprocessor-operators.md)
