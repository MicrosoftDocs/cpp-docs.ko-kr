---
description: '자세한 정보: 전처리기에 대한 지시문'
title: 전처리기에 대한 지시문
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 50691647436f492b329b6af43a626e933453d3a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213958"
---
# <a name="directives-to-the-preprocessor"></a>전처리기에 대한 지시문

"지시문"은 컴파일 전에 프로그램의 텍스트에서 특정 작업을 수행하도록 C 전처리기에 지시합니다. [전처리기 지시문](../preprocessor/preprocessor-directives.md)은 *전처리기 참조* 에 자세히 설명되어 있습니다. 이 예제에서는 전처리기 지시문 `#define`을 사용합니다.

```
#define MAX 100
```

이 문은 컴파일 전에 컴파일러가 `MAX`에 의한 `100`의 발생을 각각 교체하도록 합니다. C 컴파일러 전처리기 지시문은 다음과 같습니다.

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>참조

[원본 파일 및 원본 프로그램](../c-language/source-files-and-source-programs.md)
