---
title: 컴파일러 오류 C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 1555817de6e50ea27a021718c8b094efeaebacde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230846"
---
# <a name="compiler-error-c3551"></a>컴파일러 오류 C3551

"런타임에 지정된 반환 형식이 필요합니다."

**`auto`** 키워드를 함수 반환 형식에 대 한 자리 표시자로 사용 하는 경우 런타임에 지정 된 반환 형식을 제공 해야 합니다. 다음 예제에서는 런타임에 지정 된 함수의 반환 형식이 `myFunction` 형식의 네 요소 배열에 대 한 포인터입니다 **`int`** .

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>참고 항목

[auto](../../cpp/auto-cpp.md)
