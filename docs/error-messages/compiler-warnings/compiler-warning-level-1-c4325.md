---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4325'
title: 컴파일러 경고(수준 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 17e14d4909e4b76d6a0a71d6e77fad1d01e3f41b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311593"
---
# <a name="compiler-warning-level-1-c4325"></a>컴파일러 경고(수준 1) C4325

> '*section*' 표준 섹션의 특성이 무시 되었습니다.

## <a name="remarks"></a>설명

표준 섹션의 특성을 변경할 수 없습니다. 예를 들어:

```cpp
#pragma section(".sdata", long)
```

데이터 형식을 데이터 형식 `.sdata` 으로 사용 하는 표준 섹션을 덮어씁니다 **`short`** **`long`** .

특성을 변경 하지 않을 수 있는 표준 섹션에는 다음이 포함 됩니다.

- . 데이터

- .sdata

- . bss

- . .sbss

- .text

- .cconst

- .ssconst

- . .rdata

- .slsa 데이터

추가 섹션은 나중에 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[여기서](../../preprocessor/section.md)
