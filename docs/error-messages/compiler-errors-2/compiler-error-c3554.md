---
description: '자세한 정보: 컴파일러 오류 C3554'
title: 컴파일러 오류 C3554
ms.date: 11/04/2016
f1_keywords:
- C3554
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
ms.openlocfilehash: 39bc1a673af37d6b73941bb300d86df5f41a4704
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223180"
---
# <a name="compiler-error-c3554"></a>컴파일러 오류 C3554

'decltype'을 다른 형식 지정자와 함께 사용할 수 없습니다.

형식 지정자로 `decltype()` 키워드를 한정할 수는 없습니다. 예를 들어 다음 코드 조각은 C3554 오류를 생성합니다.

```
int x;
unsigned decltype(x); // C3554
```
